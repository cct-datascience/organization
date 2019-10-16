# OPEN Kickoff

http://arizona.zoom.us/my/dlebauer

HackMD: <https://hackmd.io/S9H9RHKoQOmMWLBZcv8Bww>

Present: Chris, David, Julian, Max, Nirav, Rob, Tony

## Agenda

1. Wrapping up TERRA REF
2. Open 
    * Review Milestones
    * Broad Objectives
4. Open Project Management
    * Meetings
    * Define Roles
    * Schedule NCSA visit to UA 
        * Week of Jan 13
    

## Remaining tasks from TERRA REF

1. Data Archiving
    * Data Publication (hosted at NCSA?)
        * Potentially at NCSA hosted by ISDA/Software Directorate
            * Only Season 4 and Season 6
            * Need MOU for hosting with Danforth/Arizona/NCSA (Rob will talk w/ Kenton)
        * Waiting on archive plan
    * Data Archiving 
        * From Storage Condo (timeline?)
            * Officially December 2019
            * Need to prioritize
        * From Nearline (timeline?)
            * Currently in read-only
            * Hard Deadline, March 2020 (machine turned off)
2. Cache Server Handoff
    * Meeting scheduled? 
    * Sean has Julian's SSH key, Julian will set up meeting.
    * Check on Globus License
    * Due Date?
    * Max has data transfer pipeline script.
    * Need to get scripts on github 
    * Max will turn scripts into services (automatic, scheduled, restartable, more reliable)
        * Q: Monitoring & alerting? (JP)
3. Web services Brapi, search ok


## Moving into OPEN

### Key Milestones

| Milestone | Due | Notes |
| -------- | -------- | -------- |-----|
| Full Catalog and database of TERRA-REF data     | Dec 31, 2019     | Led by Stylianou | 
| Lettuce 1 Dataset  | March 31 2020     |   processed & archived |
| Present Clowder + Irods at Irods meeting | June 9 2020 | | 
| **Transfer Pipeline to UA/CyVerse\***     | **July 1 2020**      | **Critical Deadline** | 
| Pipeline validation    | Sept 30, 2020   | ARPA-E Milestone; should be done ASAP after Lettuce (ie could be done by March)|
| Sorghum 1 dataset     | Sept 30, 2020     | processed & archived.       |
| Sorghum 2 dataset     | Sept 30, 2021     | processed & archived|

* David to follow up w/ Abby on first milestone 

<!--
| Text     | Text     | Text     | Text    |
-->

* **\*** Notes for July 1 2020 Milestone:
    *  _Fully implementing the pipeline from the Field Scanner at Maricopa into CyVerse pipeline is a primary objective for the next year._
    * Transfer responsibility for Gantry Cache Server to UA
        * Should be done ASAP
    * Direct all data coming from the gantry to the UA and into the CyVerse Data Store (Max lead)
        * [ ] Max to try transferring again
            * Max will push his new code next week
    * Deploy new data transfer pipeline (IRODS)
        * irods transfer
        * adding **irods indexing** is priority
        * [ ] Clowder support for IRODS?
            * Tony: Can Clowder support HTTP? (Rob: not at this time)
            * Rob: S3 support in IRODS?
                * Tony: Next version (4, December?), yes.
            * Max: Currently, there is a process which is triggered when data lands
            * Nirav: This doesn't solve the underlying problem. IRODS should manage the physical location of where the data lives. Clowder should reflect his, and not try to point to the physical place on the file system.
            * Rob: How certain is version 4 to be deployed in December?
            * Tony: Not very - no plans started yet.
            * Options:
                * WebDAV
                * FUSE (don't talk about this.)
                * Clowder supports (maybe) IRODS
    * Deploy databases, user and application interfaces at UA (BETY, Clowder). 
        * Rob: High priority
    * Convert to use of IRODS for data transfer and Data Store for data storage and/or indexing.
        * Is this a requirement?
        * will discuss at separate meeting
    * Re-implement all workflows for data product generation at UA
        * Who will do this: Julian & Chris? Is this is requirement?
        * Rob: Thinks we should move Clowder pipeline over and get working first, then do the migration
        * David: Concerned about time involved in getting Clowder pipeline working if it will be replaced anyway.
        * Julian: there is the effort to just standing something up at UA vs. scaling at UA. 
    * Deploy all standard data processing pipelines within CyVerse.
        * Who will do this? Is this is requirement?
    * Make data broadly available for analysis.


#### Notes: Pipeline validation Sept 30, 2020

- Max: Should be able to validate using first week of scanning data in March (i.e. don't need full season's data)


### Broad Objectives for UA Pipeline

1. Migrate pipeline to UA
    * Potentially split into two phases (run Clowder as is, and converting to DAG) (which could be done in parallel)
    * Max: Go-no-go in December: all sensors to Level 1; RGB through to canopy cover
    * Julian (Rob agrees): Deploying Clowder & extractors using Rob's WIP Helm charts in January would be easier than trying to do it now.
3. Use CyVerse infrastructure
    * iRods Data Store
    * VICE
4. Enable Distributed Computing
5. Make it easier for algorithm developers to contribute
    * Plot level RGB example: 
        * https://github.com/az-digitalag/dpp-extractor-plot
6. Platform independent
    * Decouple from underlying environment
    * Follow Matts' ECSS Pegasus work


### Project Management, Weekly Meetings

* Visit to UA 
    * Who? Max, Rob
    * When?
    * Agenda
* Specific Meetings
    * Open Kickoff (Oct 16)
    * Data Storage
        * Who: Julian, Blake, Sarah, David, Sean, Rob 
        * What: what data to archive on GDrive, where season 4 and 6 published data goes
    * Cache Server Handover 
        * Who: Julian, Sean
        * What: ?
        * See [TERRAREF cache server handoff docs](https://docs.google.com/document/d/1gIT7vioMxJsXUESMJQORB0lTPX9PaMHwIN0i_XtkN0U/edit)
    * Pipeline handover - Wednesdays at 11AM AZ/1PM IL time
        - Goal of meeting: reach common status between people, make sure items aren't missed. 
            - use Slack and GitHub for communications
            - Slack: TERRA REF project; tr-ua channel
            - GitHub: 
        - Who: 
            - UA: David, Julian, Chris, Jorge
            - NCSA: Rob, Max, Todd, 
        - What: 
            - Max: postmortem summary
            - When will Max (and Rob?) visit UA?            - what 
* Thursday 12-2AZ/2-4IL 'hackathons' with the larger team (algorithm writers and data users)
    * these will replace earlier Monday meetings
    * developers attend **as needed**? 
        * Max is going down in level of effort
        * What's best use of time?
    * who: extractor developers, data users, PIs and PMs
    * what: review what has been done, sticking points
* Wednesday 11-1 Sprint Planning and Review
    * Who: David, Julian, Chris, Max, Todd
    * When? 
        * Combine w/ (first 15 min of) UA sprint planning / review meetings. 
        * Next planning is Thursday Oct 17; Next review is Monday Oct 21; bi-weekly after that.
    * What?
        * Meetings are described [in this document](https://osf.io/tzmhp/wiki/Project%20Management/)
* David Weekly Checkin w/ Rob (Thurs 9AM AZ/11 AM IL) 
* Are there any additional meetings?
* Decouple new pipeline from TERRA REF? Nadia and David to make a decision
    * Fork vs Branch vs 'Import' (all keep history, but have different trade-offs)
    

## Chris's testing of workflow
https://github.com/Chris-Schnaufer/agp-test

### Misc

* New repository to track pipeline migration?

- Rob: Use this refactoring as an opportunity to update extractors to make useful for other workflows
    - Reducing redundant efforts & sharing code bases
    - Rob wants to be able to allow developers to run individual extractors on their desktops without needing Clowder infrastructure
    

---

### Roles

- Project Manager (10-20%)
    - Top level coordination across teams (Duke, DDPSC, GWU)
    - setting boundaries and expectations 
    - "Responsible for success of development and deployment of Ag processing pipelines at UA through: planning and scheduling, analyzing and managing project risk, reporting and documentation, outreach and coordination with stakeholders and other groups, monitoring progress, ensuring quality and satisfaction"
- Max
    - lots of stuff
    - irods implementation
- Todd
    - managing and running of pipelines at NCSA
- Rob
    - data management
- Chris: 
    - Technical Manager (and senior developer?)
    - Schedule, high level guidance, coordination - sprints, technical directions
    - Mentor for new project technical pm
    - Coordinate w/ GWU PM (setting boundaries)
- Julian: 
    - Tech lead (NOT A MANAGER!) and developer
    - Coming up with appropriate and feasible technical solutions
    - Ensure we keep quality high, and technical debt and incidental complexity as low as possible
    - Work closely with Max on the above two 
    - Help Chris with creative problem solving/technical solutions/processes in his role of managing expectations/setting boundaries
    - Responsible for mentoring junior developers
    - Working w/ Chris on scheduling stuff, to make sure things don't slip
- David: 
    - Product Manager/owner
    - BDFL (final say on technical choices, after considering proposals)
