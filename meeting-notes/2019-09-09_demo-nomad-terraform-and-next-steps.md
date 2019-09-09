# Pipeline, Terraform, Nomad, and next steps

2019-09-09

Participants: David, Chris, Julian

## Terraform & Nomad demo

Got the nod of approval from Chris.


## TODO

- [ ] Store data on disk (or ideally IRODS), but not Mongo (JP)
- [ ] Ask Eric about availability of Sateesh (DL)
- [ ] Flesh out CyVerse/NCSA pipeline analogues, and make architecture diagram (JP, CS)
    - See KR: 'Sketch TERRA REF architecture diagram with Sateesh'
- [ ] Investigate what's involved in replacing RabbitMQ with Makeflow (keeping everything else the same) (JP)
- [ ] Or... successful run of test data through system (JP) (???)

...talking... 

David asks Julian to figure out what to do next, leaves.

Chris & Julian discuss options. See below.


## New priorities based on bang-for-buck, and de-risking

- [ ] Setting up BETYdb on Nomad and having the extractors talk to it might be sufficient for a learning experience.
    - Kills 2 birds with one stone: 
        - Would be needed for testing end-to-end, 
        - as well as Welsch replacement
    - This would be required whatever road we take after that

Other risky unknowns/questions that would be nice to answer sooner rather than later:

- [ ] Makeflow
    - Instead of doing end-to-end test first
    - This would be instead of using RabbitMQ triggering, and would potentially involve looking at the Pegasus PoC
    - Benefits: 
        - Nirav wants it
        - We need to do this anyway for both the Gantry as well as the Drone pipeline
        - Might answer the Parallelization question below
    - Would be worth it if isn't going to take too long. Otherwise we're not using Illinois folks' expertise efficiently.
    - The goal of this exercise would be to get _'just enough'_ confidence that Makeflow will be able to run the extractors and get the data where it should be. If this looks positive then we go ahead and do it, and skip getting the RabbitMQ triggering workflow working at UA.
    - What does _'good enough'_ like for a first go?
        - Each extractor knows where its source data is
            - E.g. bin2tif: Knows where its metadata.json file is, and where at least one of the left/right `.bin` files is.
        - Each extractor stores its output in the right spot
            - E.g. bin2tif: geotiff should go to the right spot on the disk, and the updated metadata should go to Clowder (Mongo)
        - Successful completion of first extractor (based on above criteria) triggers execution of next extractor, which should also finish successfully (with correct input & output)
        - I.e. two extractors, maybe bin2tif & rgbmask
        - These extractors are 'fan-out', and should ideally run in parallel
        - Then bring them together - 'fan-in' using fieldmosaic extractor. This extractor should not run until all the rgbmask extractors have finished
        - Dummy extractors would be suitable to test this (avoids having to wait until extractors are ported to get certainty about the approach.)

- [ ] Parallelization of extractors


**Decision made - Julian's Sprint 18 is going to focus on (in no particular order):**

- Set up BETYdb on Nomad
- Proof of concept of Makeflow with dummy extractors


## How to: Successful run of test data through system - compare against NCSA results with 100% match for canopy cover

(But probably not doing this in Sprint 18, see above.)

Steps for testing:

- Deploy all necessary extractors to Nomad
    - bin2tif
    - image quality
    - mask
    - full field orthomosaic
    - ???

Have a look at slide 14, stereoTop in `TERRA REF Pipeline Diagrams.pptx`

Notes: 

- Have a look at the Pegasus workflow for what's required
- Rule checker will require a database. This is an ad-hoc PostgreSQL database, not the BETYdb database.
- Rule checker might not be required, as it's only a day's worth of data, and we don't have to check whether the data is there.
- Some of the logic is in the extractor code.

Then:

- Set up local BETYdb
- Populate/sync database from TERRA-REF
- Truncate traits table in local BETYdb database

Recommended test dataset (by DL):

- Go to <https://traitvis.workbench.terraref.org>
- Season 6
- Variable: Canopy Cover
- Pick a day - 2018-05-27

Steps to get data:

- Go to Globus
- Find all the RGB data for that date (raw data folder)
- Process that to generate 'Canopy Cover'

Now the traits table should be populated.

- Compare dump of local traits table with the one from TERRA-REF

Note: Processing a day's worth of data could take some time. Now's the time to see how that OpenStack scaling goodness is going to work.