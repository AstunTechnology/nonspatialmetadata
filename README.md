# Non-Spatial Metadata for Geonetwork 3.4.x onwards

**WORK IN PROGRESS**

Changes to geonetwork core code and the ISO19139 schema plugin to store non-spatial metadata in Geonetwork 3.4.x onwards and output as rdf suitable for harvesting into data.gov.uk.

## Installation

### Building from Source

Copy the root `web`and `schemas` folders over those in your build directory before building.

### Deploying in a pre-built application

Copy `web/src/main/xslt` into `/var/lib/tomcat8/webapps/geonetwork` and `schemas/iso19139/src/main/iso19139` into `[data_dir]/config/schema_plugins`

Copy `xml_iso19139-schemaupgrade.xsl` into the `process` folders of any schemas you have records you wish to convert. 

Add the following to `/var/lib/tomcat8/webapps/geonetwork/catalog/config/batch-cfg.json`:

	{
    "key": "xml_iso19139-schemaupgrade",
    "type": "fixed-params",
    "params": []
  	}

Add the following to `/var/lib/tomcat8/webapps/geonetwork/catalog/locales/en-custom.json`:

	"xml_iso19139-schemaupgrade.xsl":"convert to ISO19139 non-spatial"

Restart your web service. The conversion script should then be available in Admin console -> Tools -> batch process

## Simplified Editor

A simplified editing interface is available for non-spatial records and will be the default if you edit a converted record. It contains in-built guidance and shows only the fields required for non-spatial records. The advanced editing view has been disabled, but xml view is still available. The online resource wizard and suggestions wizard have also been disabled.


## Samples

The folder `test records` contains an example record that can be used for testing purposes.

## Harvesting

Use the following form of endpoint in (say) DGU, where `_cat=nonspatial` is a filter

geonetwork/srv/eng/rdf.search?_cat=nonspatial

Note that you may need to reindex the catalog (or the records you wish to update) for changes to show in the rdf

## Field mapping

See https://github.com/ckan/ckanext-dcat#rdf-dcat-to-ckan-dataset-mapping for the mapping from dcat to ckan

* The dcat:Catalog section comes mainly from catalog settings, such as the Catalog Name and Organisation in the Admin Console -> Settings
* The catalog language setting comes from the language used for the catalog, eg the 'eng' in the URL
* Licence must be exactly 'Open Government Licence' (<dct:license rdf:resource="https://webarchive.nationalarchives.gov.uk/+/http://reference.data.gov.uk/id/open-government-licence"/>)
* Update Frequency maps to "accrualPeriodicity" and uses the following set of terms https://project-open-data.cio.gov/iso8601_guidance/#accrualperiodicity


## TODO

* Add license and update information to distribution section
* Add data creation and update dates (aka resource:issued and resource:modified) to distribution section
* Create reduced editor view in the ISO19139 schema plugin
* Create templates
* Produce guidance on harvesting in data.gov.uk (some metadata comes from settings in data.gov.uk rather than the records themselves)


