# AZMet meeting notes

2020-07-06

Present: David, Chris S, Emily, Matt Harmon, Matt Rahr, Toby Torrey

HackMD link: <https://hackmd.io/@julianp-diag/H1MbLk-JP>

## Notes

Matt Harmon is leading this effort. He reports to Toby.

Needs
- want to minimize operator involvement
    - automated QA/QC
        - routines based on Bruce's current (daily) visual assesment 
        - minimize need for operator intervention 
    - calculation of confidence intervals
    - gap-filling
    - use historical data to flag outliers
- transition to modern platform; make it easier for Bruce's replacement to focus on new data products rather than keeping system maintained.
    - RDBMS
    - data versioning
- what does weather underground do w.r.t. checks?


First site at Campbell ag Center
State run mesonet. 
- Most sites have multiple stations per site.
- This would benefit the data quality
    - how can we use other data sources to qc and improve / gapfill data 

- "Campbell Scientific Data Loggers"
- Two kinds of loggers (??)
    - Q: What are the differences? 
    - A: File formats
- Two different text formats
    - Q: What formats?
- QuickBasic 64
    - Technology for doing processing
    - format checks, scientific calculations
- DOS batch files
- 60% is file management
- Once done, data is pushed to website
    - <https://cals.arizona.edu/azmet/>
- If sensor site is down...???
    - Manual intervention
- Bruce uses various visualization tools to find irregularities
- He will then use various tools to manually intervene
- Matt: Current best practices is to assign confidence intervals, and if changes are needed, do so in a way which is transparent (don't modify original data)
- Historically those kinds of changes were not transparent
- There are notes on a day's readings, but not what exactly what happened
- E.g. 
    - If there is a heat spike during a maintenance window, but Bruce decides it will not affect the day's high, he will let it through
    - Phoenix greenway, sprinkler systems combined with rain (Is it sprinkler? Is it rain? Both?)
- Takeaway: Current system requires a lot of operator intervention
- Main goal: Minimal operator involvement
    - Firstly: Move to a more modern platform (flat text files to RDBMS)
    - Identify anomalies automatically (e.g. 130 degrees in Tucson)
- Wish list:
    - Mobile website to alert operators
    - Somebody asked for an app (justified as more secure, but Matt H. not convinced there's much of a difference)
- Current system requires maintenance every day
    - Matt H wants to eliminate daily intervention
    - Q: What is the kind of maintenance required?
- Toby:
    - Flat files -> Database
    - Provide an API for more sophisticated access
    - Provide continuity for users who expect flat text files (Generate flat files from database? Or keep flat files and create a parallel pipeline?)
- Q: How many end users? Who are they?
- Toby: They do have some tracking who's using
- Matt: _Must_ maintain legacy format access, but reduce operator intervention 'to the floor'
    - If there is staffing, human involvement should be 'talking to people', equivalent of 'sales', and community relationship
- Hardware maintenance not being done as often as originally envisioned
- Q: David - what kind of technologies have you looked at? (Databases & APIs)
    - Answer: (Toby) Campbell Scientific products, LoggerNet, but mainly want to move to more modern scripting
    - Answer: (Matt H) LoggerNet -> database, cost prohibitive ($2200 license). Oracle is not an option, Windows-based, but there is some Linux solution
    - Looked at MySQL
    - 25 rows of day, per station
    - 29 stations
    - Better options? 
    - Note: See <https://www.timescale.com/>
- David: Mentions some visualization solution with combination of open source and proprietary tools
- David: Q: What happens to text files? Are they just dropped?
    - Matt H: AFAIK Bruce doesn't dump & wipe raw data from stations
    - Toby: Mix of older & newer devices. Newer devices keep much more (currently all) of raw data
- David: If somebody wants to update the algorithms on the devices, do they have to go there?
    - Q: Toby - Can be done remotely
- David: Can't we keep all the data, higher resolution?
    - Toby: They pull once an hour (actually once 24 hours). Restriction in past was high Verizon data bills due to not being able to handle reliably disconnecting modem connections. But it's not a lot of data in modern terms.
- Matt: Wants to demonstrate to Bruce that his legacy will be maintained
- David: As discussed with Emily, it's not clear how to to cite the data
- Q: LoggerNet license - is that monthly, yearly, one-off? 
    - Answer: Also evaluated LNDB (LoggerNet Database)
        - <https://www.campbellsci.com/lndb>
        - Initial cost: $1900 
        - Maintenance cost: $1200 per year (or every time an upgrade is needed?)
- Q: LoggerNet, is it pulling 
    - Matt H: 
        - Firmware that writes data tables 
        - Data Logger: Creates CSV file
        - Code that converts voltage readings to processed data is in some some proprietary Campbell Scientific programming language
        - LoggerNet can be modified to pull down 'raw data'
    - Matt R: Only limitation on pulling down more data/more frequently is the cellular data
        - Can use UA's purchasing power

