# Meeting: ACIC Makeflow collaboration

2020-03-10

Present: John X., Emmanuel, Chris, Michele, Sateesh, Julian


## Agenda

- Chris & Julian to get an understanding of the current state of the Makeflow pipeline


## Notes

Julian asks:

- What is the current state of the workflow? (high level)
- Which parts of pipeline are functional?
- Does it scale?
    - RGB (Emmanuel): 4-5 hours per field/scan, starts plateauing at 60 workers
    - FLIR (Michele): 4-5 hours per field/scan, starts plateauing at 33 works
    - 3D: 4 hours per field/scan (vs 5 hours for Sorghum)
- What about the field mosaic bottleneck?
    - [GitHub: Clip Level 1 images to plot, analyze, combine #356 ](https://github.com/terraref/computing-pipeline/issues/356)
- What's missing?
- Next steps?

Documentation (needs updating): <https://phytooracle.readthedocs.io/en/latest/contents.html>


## Current state

- Master is on an Atmosphere virtual machine
- Bundling explanation
- Data transfer explanation
- Plans to migrate everything to HPC
  - Will still be able to be run on virtual machines
- Michele: Looking forward to partition WorkQueue workers for more parallelism
- Michele: Used to have to start all workers at the same time
    - Now it looks like you can start them and start more later and it keeps working
    - Not sure what changed
- John: Makeflow WorkQueue authentication
    - Auth between Makeflow as a WQ master and WQ workers
    - Run naked without password during development **(BAD)**
    - Could use Makeflow's WQ auth, which uses a password file
    - Additional auth/restriction could be added if necessary
- John: Nginx auth
    - Currenly nginx auth is just HTTP(S) auth with username & password

## What's missing (in order to kick off workflow based on tars in IRODS)

- Orthomosaic algorithm
    - To make it work with lettuce
    - WIP
    - Specifically for RGB
    - Testing in progress
    - May not be useful for other crops like sorghum (Chris)
        - But it might work, and it's worth testing (Emmanuel)
- Reload NGINX
    - Pointing it at the files we'll be processing
    - Where tars from IRODS are extractd
    - Michele also puts all the source code in there
    - John X. says it's not necessary, but it's convenient
    - John: check permission of files
- The resulting files just sits in folder
    - Needs to be tarred & uploaded to IRODS
- The intermediate results
    - Mostly ignored
    - Except for RGB where Emmanuel is keeping them and keeping them along with final results
- Michele: Sometimes the HPC workflow doesn't work
    - Something about 'image not recognized' (Singularity)
    - Currently the workaround is to Ctrl-C, clear Singularity cache, resubmit
    - Sometimes just resubmitting works
- John: Preferably uses WQ workers instead of WQ factory
    - WQ factory sometimes has bugs causes it not launching the targeted number of workers (not sure fixed yet)
    - we have a script for this https://github.com/uacic/PhytoOracle/blob/bundle/stereoTop/launch_wq_workers.sh
    - `pkill` afterwards
- John: Monitoring
    - `makeflow_status` from CCTools to check progress of pipelines, and num of workers
        - This utility will crash once in a while (something about floating point conversion), so needs to restart it after crash, not sure if they fixed it
    - `work_queue_status` from CCTools to check progress and num of workers
        - This pull stats from catalog server, useless if does not use catalog server
    - `netstat` to check num of workers, and connections status
        - If Makeflow is being over loaded, pending (broken) worker connections will usually show as LAST_ACK/TIME_WAIT
    - `htop` on workers to check CPU load
        - Almost everything is single-threaded, so one task will basically use 100% of a core
- John: WorkQueue Worker param worth pay attention
    - `-M` project name, the name to report to catalog server
        - if specified, will use project name instead of raw IP:port
    - `-C` specify which catalog server
    - `-b` the max retry interval if fail to connect to master
    - `-t` timeout
        - `--idle-timeout`
        - `--connect-timeout`
    - `-s` base path to create tmp working directory for workers
        - ideally point to somewhere with large amount storage (e.g. `/scratch`), so that the disk is not filled by temp data
        - default to `/tmp` which is usually part of `/`
    - `--wall-time` max lifetime of a worker, worker will kill itself after this time


## Action items

- [x] Documentation for bundling of data
    - See <https://github.com/uacic/PhytoOracle/tree/master/stereoTop>
    - Note: Bundling is used for all the pipelines
    - Number of bundles is roughly proportional to number of workers (e.g. 2 bundles per worker)
    - Note: For dynamic scaling of workers make sure that you high ratio of bundles to worker
- [ ] Parsing: Check if new version of Makeflow parsing performance is better (John)
- [ ] Nice to have: Automated provisioning of workers
- [ ] John: Singularity Images as input files
    - This is to avoid image corruption due to race condition of multiple concurrent pull from docker-hub
    - Currently image is pulled manually before starting workqueue worker on worker nodes, not ideal for automation
    - Appears to be a Singularity only issue, Docker does not have it
- [ ] John: Nice to have: Better monitoring tools
    - Currenly monitoring tools are kind of scattered, and requires a lot of attention/babysitting


## Retrospective (later)

- Was Makeflow a good choice? Would Snakemake be better?
    - John: Snakemake has a better & comprehensive CLI frontend
    - John: Makeflow has WQ as backend which enables dynamic scaling, while Snakemake does not
        - But Snakemake can be extended by implement a custom executor with WQ, if the executor is implemented using WQ lib as is, that means same single-thread problem would occur. (Warning, not a easy task)
    - John: Makeflow has parsing performance problem, Snakemake might not (not aware of at least, never tried large scale on Snakemake)
    - John: Makeflow is static in terms of specifying workflow (needs to specify exact filename of each files), Snakemake is more dynamic
        - static could mean better monitoring
        - dynamic could mean more flexability in writing workflow
- John: Nginx vs Others (e.g. Chirp by CCTools)
    - Nginx is easier and more convenient to stand up
    - Chirp supports more auth methods (e.g. Globus, Kerberos)
- John: Public (by CCTools Lab) or Private Catalog Server
    - We make use of catalog server to broadcast Makeflow masters to public, and have workers look up IP of master through catalog server via project name, instead of giving workers the raw IP of master
    - Could stand up a private catalog server rather than using the public one