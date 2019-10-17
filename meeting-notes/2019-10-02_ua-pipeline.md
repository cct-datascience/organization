# UA Pipeline

2019-10-02

Present: Chris, David, Julian, Tony, Sateesh

HackMD link: https://hackmd.io/E4mtCmlETR2akIQWNS8KEg

## THREDDS server at CyVerse?

- T: On the list of priorities.
- D: Anybody else interested?
- T: Yes, Laura Condon. Also somebody in Colorado in the NEON project. Meeting them this Friday.


## IRODS metadata mirroring

From last meeting: <https://github.com/az-digitalag/organization/blob/cd3dca53f75211a6140d474729788c758856263b/meeting-notes/2019-09-18_ua-pipeline-update.md>

> J: Propose putting Clowder & BETYdb metadata experts and IRODS metadata experts in the same room and seeing if the structures map at all, and whether it's infeasible, or worth trying to map some metadata to IRODS.
    
D: Will share Clowder metadata schema in the notes

![](https://i.imgur.com/UdLSXDh.png)

## Chris

- C: Not working on anything specifically TERRA REF related at the moment

- C: Will work on standardizing the extractor containers.

## Julian

- Makeflow PoC went well
- Working on test data through local Clowder setup

- J: Asks Tony, what's the most reliable way to copy data from cache server to CyVerse

- J: Should we use a workflow system to synchronize transfer of data to avoid data being uploaded to NCSA, and it's deleted before data is transfered to IRODS?

- [ ] Look at https://github.com/terraref/computing-pipeline and globusuploader service (J)

- Decision: Going to try to make Globus transfer work, get processing working, then figure out different transfer mechanism.

- [ ] Q: What's the state of the gantry cache server 60% 'low-water mark' issue? (J)

- C: Will meet with Edwin about transfer to figure out status.


