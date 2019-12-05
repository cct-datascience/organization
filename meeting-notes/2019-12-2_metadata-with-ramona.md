# Metadata Meeting with Ramona
### 2019-12-2

Present: Emily Cain, Ramona Walls

### Notes

* Discussed and shared the Cornell best practices for writing "readme" style [metadata](https://data.research.cornell.edu/content/readme)
* Metadata should be human-readable (like the Cornell template) and also computer-readable
    * JSON / XML / [EML](https://www.dataone.org/software-tools/tags/EML)
    * The University Library may not require computer-readable metadata because they want to make it easy for users to publish data, but some researchers use web scrapers to find data, so being deliberate about using keywords in the description is extremely important.
    * Additional metadata above and beyond the basic requirements for a DOI is ideal.
    * Ramona will be re-learning EML so can be a resource in this area, in addition to Jeanette.
* Reproducing code and data transformations
    * Executable Jupyter Notebook ([Binder](https://mybinder.org/) button would be great)
    * `.py` script
* Every dataset / data file needs to be described
    * If image datasets are large and variegated, for example, people should be able to pinpoint and find exactly what they need. 
    * Some researchers may only be interested in a specific cultivar, specific time period, etc.
    * For tabular data, every column should be described in a data dictionary, without making unreasonable assumptions about user / domain knowledge. 
* Gene Identifiers
    * If ever working with data for actual specimens, specimen-level identifiers required
    * If possible, they should be globally unique
        * [IGSN](http://www.geosamples.org/aboutigsn) (International Geo Sample Number) expanding
* Always keep in mind how the data will be used, if curating for a specific purpose (i.e., predictive machine learning model)
* If an ARK (Archival Resource Key) is required, come back to Ramona
* CyVerse already has the code for schema.org, if the University Library is going to be using that
* Datasets are considered a valuable research output

### Resources, Guides, & Further Research
* Publishing Data with [CyVerse Data Commons](https://wiki.cyverse.org/wiki/display/DC/Publishing+Data+through+the+Data+Commons)
* CyVerse [DOI Request Quickstart](https://cyverse-doi-request-quickstart.readthedocs-hosted.com/en/latest/organize.html)
* DataONE [Best Practices](https://www.dataone.org/best-practices)
* [schema.org](http://schema.org/)
* Sequence Identifiers - [NCBI](https://www.ncbi.nlm.nih.gov/genbank/sequenceids/)
* [GigaScience](https://academic.oup.com/gigascience) - open access, open data, open peer-review journal focusing on big data research from the life and biomedical sciences
