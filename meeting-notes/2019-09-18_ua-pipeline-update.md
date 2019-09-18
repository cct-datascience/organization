# UA Pipeline 

2019-09-18

Present: Chris, David, Julian, Sateesh, Tony

HackMD link: <https://hackmd.io/8en350gfQnafquZpsGcf1Q>

---

## Current status of Globus?

J: Last known, Edwin had set it up and ready to use, then we talked to Nirav (halted), and we still have to run benchmarks.

D: Tested some Globus transfer, and worked for bit, then didn't. Endpoint is down.

T: Maintenance last week, rebooted servers, so Globus software might not have come back up afterwards.

D: Also found out that GDrive @ UA has unlimited storage, and might store TERRA-REF data there long term. Can IRODS integrate with GDrive?

T: Next year CyVerse Data Store will be able to use any S3 compatible service (like GDrive) as a backing store.


## Status standing up pipeline

J: Need to test with larger data, that will take a day or more to process.

Postponed in favor of Makeflow PoC and BETYdb on Nomad this sprint.

Made progress on BETYdb on Nomad, another few hours remaining.

Will catch up with Sateesh about combining efforts on Makeflow PoC.


## Provide access to products like NCSA currently does

D: Waiting till after MVC to make calls on some products

C: Segregating by 'level' of the data?

D: 'Plant people' will want to use API endpoints, and 'computer people' will want the files.

L0: Discarded (maybe, unless GDrive is an answer)

L1: Contains all the information of the raw (L0) data

L2: Same resolution as L1, but 'derived' (e.g. greenness)

L3: Aggregated. Standard way is 'by plot' and stored in database or CSV files.

Exceptions to discarding L0 data: PNG files from the laser will be kept. Computer vision people want it.


## BETYdb & Clowder

D: What does it look like when mapping the functionality of these databases to native IRODS functionality?

T: In theory you can add PostGIS extension to IRODS metadata database, but gut instinct is to keep those databases separate.

D: Is there a way to keep metadata in sync between IRODS and other databases?

T: That was on the roadmap, but it seems to have fallen by the wayside (QueryArrow). Might still happen. Something blocked it.

J: Propose putting Clowder & BETYdb metadata experts and IRODS metadata experts in the same room and seeing if the structures map at all, and whether it's infeasible, or worth trying to map some metadata to IRODS.









