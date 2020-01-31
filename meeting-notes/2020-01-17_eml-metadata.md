## EML & Generating Metadata
### January 17, 2020 

Present: Emily, David, Jeanette, Ryan

### Resources
* [Arctic Data Center Tutorial](http://training.arcticdata.io/materials/arctic-data-center-training/programming-metadata-and-data-publishing.html)
* [EML R Package documentation](https://CRAN.R-project.org/package=EML)
  * [Tutorial](https://cran.r-project.org/web/packages/EML/vignettes/creating-EML.html)
* [Slides](http://training.arcticdata.io/materials/arctic-data-center-training/03-best-practices-data-metadata.pdf) for metadata best practices
by [Matthew B. Jones](https://orcid.org/0000-0003-0077-4738) with [Arctic Data Center](https://arcticdata.io/)
* [emldown package](https://ropensci.org/blog/2017/08/01/emldown/)
* [dataspice package](https://docs.ropensci.org/dataspice/) (json)

### Notes (example instructions from [Arctic Data Center Tutorial](http://training.arcticdata.io/materials/arctic-data-center-training/programming-metadata-and-data-publishing.html))

* Arctic Data Center has a form which generates an EML file for you from the information you enter, but you can also 
generate your own metadata using the R packages [dataspice](https://docs.ropensci.org/dataspice/) and [EML](https://CRAN.R-project.org/package=EML)
* Specific submission requirements / obtaining a DOI will depend on the data repository 
* Use [emldown](https://ropensci.org/blog/2017/08/01/emldown/) package for pretty, human-readable metadata using R Markdown

### EML Package Notes
* constructor functions help generate metadata
```
me <- eml$individualName(givenName = "Jeanette",
                         surName = "Clark")

doc <- list(packageId = "dataset-1", system = "local",
            dataset = eml$dataset(title = "A minimial valid EML dataset",
                                  creator = eml$creator(individualName = me),
                                  contact = eml$contact(individualName = me)))
```
* The `write_eml` function would then generate the following metadata:

```
## object and file location / name for arguments

write_eml(doc, "files/simple_example.xml")

## "simple_example.xml" file

<?xml version="1.0" encoding="UTF-8"?>
<eml:eml xmlns:eml="eml://ecoinformatics.org/eml-2.1.1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:stmml="http://www.xml-cml.org/schema/stmml-1.1" packageId="id" system="system" xsi:schemaLocation="eml://ecoinformatics.org/eml-2.1.1/ eml.xsd">
  <dataset>
    <title>A minimial valid EML dataset</title>
    <creator>
      <individualName>
        <givenName>Jeanette</givenName>
        <surName>Clark</surName>
      </individualName>
    </creator>
    <contact>
      <individualName>
        <givenName>Jeanette</givenName>
        <surName>Clark</surName>
      </individualName>
    </contact>
  </dataset>
</eml:eml>
```

* Check your work regularly with `eml_validate(doc)`
* More detailed information can be added. Using the `me` object as an example, you can also add:
  * organizationName
  * electronicMailAddress
  * userId (e.g., orcid id)
* `set_methods` function can parse a text or markdown document and insert into the methods section
* `set_attributes` function can take a `data.frame` with your variables and attributes
* An example using time, temperature, and sitename variables:
```
atts <- data.frame(attributeName = c("time", "temperature", "sitename"),
                   attributeDefinition = c("time of measurement", "measured temperature in degrees Celsius", "plot location"),
                   unit = c(NA, "celsius", NA),
                   numberType = c(NA, "real", NA),
                   formatString = c("HH:MM:SS", NA, NA),
                   definition = c(NA, NA, "plot location"))
```
* To generate `attributeList` to describe the variables in a `dataTable`:
```
doc$dataset$dataTable$attributeList <- set_attributes(attributes = atts,
                                                      col_classes = c("Date", "numeric", "character"))
```
