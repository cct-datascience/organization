# ACIC Final Project

2019-10-07

Present: Chris, David, Duke, Eric, Julian, Nirav, Sateesh (Parker, arrived at 15:38)

Link: <https://hackmd.io/Q7dOECIoQimZ0BZFxlDS5Q>

Also see Eric's agenda & notes: <https://docs.google.com/document/d/1o3h4kPYoFItnEVM64d_brZ54MDpsAEl_29ITfUHef9o/edit?pli=1>


## Notes

- Project to start at the end of this month and final presentations: 12/15/2019
- Nirav: Let's have a meeting about what the 'final' workflow is going to look like (Globus vs IRODS).
- David: Wants to figure out what we need to get ready for the class.
- Nirav: Keep as much data local as possible
    - Possibly a containerized PostGIS database close to the workers
    - Or use a JSON dumped file (See Pegasus example)
- Chris: Will it include fault tolerance, scaling, etc.?
    - Eric: Yes.
    - Nirav: This should be handled by workflow management system.


## TODO

- [x] Ask Edwin for path to files transferred into data store (Julian)
    - Edwin says IRODS indexing not happening yet, and we should talk to Tony. On the storage node the physical files are at `/irods_vault/terraref-ds06`
- [ ] Take next 4 weeks to write up a statement of work, with requirements & deliverables, as though we were outsourcing to a third party (Chris & Julian, with help from David & Duke)
    - Involve Sateesh in iterations


## References

- 2015 ACIC project: <https://github.com/acic2015/findr>
