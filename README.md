# Non-Spatial Metadata for Geonetwork 3.4.x onwards

**WORK IN PROGRESS**

Changes to geonetwork core code and the ISO19139 schema plugin to store non-spatial metadata in Geonetwork 3.4.x onwards and output as rdf suitable for harvesting into data.gov.uk.

## Installation

### Building from Source

Copy the root `web`and `schemas` folders over those in your build directory before building.

### Deploying in a pre-built application

Copy `web/src/main/xslt` into `/var/lib/tomcat8/webapps/geonetwork` and `schemas/iso19139/src/main/iso19139` into `[data_dir]/config/schema_plugins` and restart your web service.

## Samples

The folder `test records` contains an example record that can be used for testing purposes.

## Harvesting

Use the following form of endpoint in (say) DGU, where `_cat=nonspatial` is a filter

geonetwork/srv/eng/rdf.search?_cat=nonspatial

Note that you may need to reindex the catalog (or the records you wish to update) for changes to show in the rdf

## Notes

See https://github.com/ckan/ckanext-dcat#rdf-dcat-to-ckan-dataset-mapping for the mapping from dcat to ckan

* The dcat:Catalog section comes mainly from catalog settings, such as the Catalog Name and Organisation in the Admin Console -> Settings
* The catalog language setting comes from the language used for the catalog, eg the 'eng' in the URL
* Licence must be exactly 'Open Government Licence'
* Update Frequency maps to "accrualPeriodicity" and uses the following set of terms https://project-open-data.cio.gov/iso8601_guidance/#accrualperiodicity

## TODO

* Add license and update information to distribution section
* Create reduced editor view in the ISO19139 schema plugin
* Create templates
* Produce guidance on harvesting in data.gov.uk (some metadata comes from settings in data.gov.uk rather than the records themselves)


