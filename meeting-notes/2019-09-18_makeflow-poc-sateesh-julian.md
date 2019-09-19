# UA Pipeline Makeflow Proof-of-Concept

2019-09-18

Present: Julian, Sateesh

Link: <https://hackmd.io/CuBin64GTZuII_GouvzK0w>


## Goals

- [x] Knowing enough to know where to start with dummy extractors


## Background

bin2tif docker repo:
https://github.com/sateeshperi/terra_pilot

Julian's goals for PoC:

<https://github.com/az-digitalag/organization/blob/master/meeting-notes/2019-09-09_demo-nomad-terraform-and-next-steps.md>

> The goal of this exercise would be to get 'just enough' confidence that Makeflow will be able to run the extractors and get the data where it should be.


> - What does _'good enough'_ look like for a first go?
>     - Each extractor knows where its source data is
>         - E.g. bin2tif: Knows where its metadata.json file is, and where at least one of the left/right `.bin` files is.
>     - Each extractor stores its output in the right spot
>         - E.g. bin2tif: geotiff should go to the right spot on the disk, and the updated metadata should go to Clowder (Mongo)
>     - Successful completion of first extractor (based on above criteria) triggers execution of next extractor, which should also finish successfully (with correct input & output)
>     - I.e. two extractors, maybe bin2tif & rgbmask
>     - These extractors are 'fan-out', and should ideally run in parallel
>     - Then bring them together - 'fan-in' using fieldmosaic extractor. This extractor should not run until all the rgbmask extractors have finished
>     - Dummy extractors would be suitable to test this (avoids having to wait until extractors are ported to get certainty about the approach.)


Rules:

- Download data 
- bin2tif converter


## Notes

- Sateesh showed master & worker on different machines and data moving between them.
- Julian can take it from here.
- Sateesh will show Docker integration later.


## TODO

- [ ] See Container Camp 2018 for Makeflow and CyVerse

