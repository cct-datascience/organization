# Mats and Makeflow pipeline review

HackMD URL: <https://hackmd.io/2OWxlr1PSUKNd_4xCacCGA>

2020-03-11

Present: Mats Rynge, Chris, David, Emmanuel, Michele, Julian

rynge@isi.edu

## Notes

Incremental compute (don't recalculate results)

- Makeflow should have support for this
- Maybe using IRODS integration

Triggering

- airflow - good framework for triggering logic & nice interface 
- pachyderm

Should email / notify when workflows fail

CWL = would stay away from
- pegasus has an importer but won't natively run it
- how would you define a workflow?

[nf-core](https://nf-co.re/)

- Repository of workflows with metadata

Abstract data transfer/storage (See references to Parrot & Chirp)

- In Pegasus they have input & output URLs (e.g. `s3://`, `irods://`)
- Idea: Nest the main Makeflow workflow inside one that does the data transfer?
- Pegasus sometimes use data staging & transfer servers


## Action items

- [ ] Ask CCTools people about triggering/cron
- [ ] Create diagram of proposed architecture and review w/ cctools team


## References

- [CCTools - Catalog server](https://cctools.readthedocs.io/en/latest/catalog/)
- [CCTools - Parrot](https://ccl.cse.nd.edu/software/parrot): Some hesitation about reliability; maybe worth checking out 
- [CCTools - Chirp](https://ccl.cse.nd.edu/software/chirp): Sounds like something that Condor has
- [Pegasus - Data Transfers](https://pegasus.isi.edu/documentation/transfer.php)
- [Pegasus - Data Staging Configuration](https://pegasus.isi.edu/documentation/data_staging_configuration.php)