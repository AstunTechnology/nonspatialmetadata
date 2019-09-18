# Non-Spatial Metadata for Geonetwork 3.4.x onwards

**WORK IN PROGRESS**

Changes to geonetwork core code and the ISO19139 schema plugin to store non-spatial metadata in Geonetwork 3.4.x onwards and output as rdf suitable for harvesting into data.gov.uk.

## Installation

### Building from Source

Copy the root `web`and `schemas` folders over those in your build directory before building.

### Deploying in a pre-built application

Copy `web/src/main/xslt` into `/var/lib/tomcat8/webapps/geonetwork` and `schemas/iso19139/src/main/iso19139` into `[data_dir]/config/schema_plugins` and restart your web service.

