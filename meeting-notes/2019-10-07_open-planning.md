# OPEN planning 

2019-10-07

Present: Chris, David, Julian

HackMD: <https://hackmd.io/QiX_1aW5SqyUz-CL9mi3Xw>

## Agenda

* strategy for NCSA’s role
    * Currently have funding for Max at 30%, Todd at 20%, $20k storage, and a few trips/year from UIUC to UA
    * What is value of NCSA running the pipeline there vs all hands on deck here?
* leading the project management and weekly meetings
    * Thursday 12-2 'hackathons' with the larger team (algorithm writers and data users)
    * Sprint planning and review - should we invite Max and Todd to ours?
* schedule (who, when, agenda) meeting to plan the pipeline handover
* schedule (who, when, agenda) meeting to plan data archiving
    * Who: sean stevens, automated globus transfers to GDrive
    * prioritize data sets for archiving
* what is possible w/ Eric’s class for their final project
    * he wants to stand up multiple pipelines - is this feasible? 
    * See [his proposal outline](https://docs.google.com/document/d/1o3h4kPYoFItnEVM64d_brZ54MDpsAEl_29ITfUHef9o/edit?pli=1) 
* specific repo to track migration activities?

## Decisions

- Kickoff meeting ASAP
- Workflow orchestration:
    - Use Makeflow
    - specify in CWL to make them portable
- Roles
    - PM (talk to Sangita - see below). 
        - Top level coordination across teams (Duke, DDPSC, GWU)
        - setting boundaries and expectations 
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
- Planning Meetings
    - Open kickoff
        - Review notes from this meeting
    - Data storage
        - who: Julian, Blake, Sarah, David, Sean, Rob 
        - what: what data to archive on GDrive, where season 4 and 6 published data goes, 
    - Pipeline handover
        - Goal of meeting: ?
        - who: 
            - UA: David, Julian, Chris
            - NCSA: Rob, Max, Todd, 
        - what: 
            - Max: postmortem summary
            - When will Max (and Rob?) visit UA?
            - what 
- Weekly Meetings
    - Thursday Hackthons (12-2), combines Monday 12-1 End user
        - who: extractor developers, data users, and us
        - what: review what has been done, sticking points
    - Infrastructure Team Sprint Planning and Review 
        - who: our team + Max and Todd 
        - when: during our weekly planning / review meetings. Break into chunks (Max & Todd for first 15 min)

## TODO

- Have an initial meeting w/ Sangita 
    - define her roles
    - define our needs w.r.t proj. management and coordination across teams
    - regular meetings w/ Sangita and Duke
- make sure we are meeting goals, facilitate interactions w/ other groups 
- Review TERRA REF postmortem

- [ ] Get milestones from David (Julian)
- [ ] Investigate tools/processes as alternatives to meetings (Julian & Chris)


## Background

- Project: The next phase of the TERRA REF project
- Funder: ARPA-E
- Time horizon: Two years
- Goal: Process the data coming off gantry (on CyVerse platform)


## References

![](https://i.imgur.com/QeiXI2D.jpg)
