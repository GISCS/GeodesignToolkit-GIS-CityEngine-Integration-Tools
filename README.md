# CityEngineToolKit-GeodesignToolkit
Summary:
     This document discusses a series of tools that were created to enable data-driven design to support large-scale scenario planning projects. These tools are intended to integrate GIS and CityEngine to enable the creation of large amounts of 3D content to support urban planning/geodesign projects. The content created can be used to create images as part of cut sheets (to be used with data-driven pages), or linked to web content in web maps (by providing content for pop-ups or web scenes to link to). The focus of the workflow proposed here is streets, but the scripts also support projects related to buildings/lots/zoning visualization.
Intent:
     The intent of these tools is to enable data-driven design on a massive scale by leveraging GIS and CityEngine in conjunction. There are great examples of how GIS data can be leveraged to create great 3D content to support transit oriented development, scenario planning efforts, or even an aviation facility's operations. However, preparing this data often involves gathering and processing aerial imagery, high-resolution terrain data, georeferenced footprints/planimetric buildings, and so on to create a complete urban model. My point is that building context for a 3D urban model takes time: so much time that it is hard to justify in a project-oriented setting without a long-term interest in a certain area.
 
However, the idea behind these tools is to make context be provided by associating content to an individual entity either being displayed  within a web map or as part of cut sheets associated with the entity. So the context is provided by your application, and the selected records (streets/lots/buildings) are enabled to show pop ups or hyperlinks that go to their associated content. In some contexts, this leads to massive time savings, and enables a larger scale to work with. The reasons why this might be preferable include 1) web maps allow you to efficiently share large sets of data by compartmentalizing 3D content to only be shared when it is inspected in the web map (similar in concept to tiling GIS data) and 2) there is not as much time dedicated to preparing and gathering information that supports sharing 3D urban scenes thus enabling more time to focus on analysis or the story your application is trying to tell. Generally, the main idea is using CityEngine for what it is really good at: creating content, unimaginable quantities of content.
![alt text](https://geonet.esri.com/servlet/JiveServlet/downloadImage/102-7343-28-166685/output_Gdh5ev.gif "Output Example")

# Tool Breakdown:
     The 6 python scripts within the CityEngine Tool Kit are broken down by software to be used with:
ArcGIS
PrepareCEStreetAssociations.py: This tool is designed to create a standard geometry to be imported by CityEngine and then used to drive rules as part of a geodesign methodology to create data driven street models.

PrepareCELotAssociations.py: This tool is similar to the previous one (it creates standard geometry for CityEngine to import), except it is used with polygons instead of lines. This tool is designed to take in polygon lot files that will be simplified into squares of a desired area, or area set by a field.

PrepareCEBlockAssociations.py: Similar  PrepareCEStreetAssocations, but creates several lines in a templated featureclass rather than one line. This tool enables the exploration of transportation and land use scenarios simultaneously at very large scales.

PopulateStreetParameters.py: This tool takes a feature class and adds street parameters and core complete street rule attributes to enable a feature class to drive CityEngine street rules.

SplitFeaturebyAttribute.py: This script is designed to take a field and use its unique values to explode a feature class into multiple feature classes within a selected workspace. (Useful for applications outside of this one, inspired by the USGS script here).


# CityEngine

CEBatchWebSceneExport.py: Batch export of web scenes of individual CityEngine Layers to create consumable content. Example at this link.

CEBatchLayerImageExport.py: Batch export of snapshots of individual CityEngine Layers to create consumable content. All of the cross section examples from this script are in the "BatchExportImages.zip" attached.

CESelectLayerByAttribute.py: Select layers in CE Scene based on an attribute within the data. For batch layer editing and control.

For more information about the tools read the help documents within the "Help" directory.
 
# Limitations:

Cross sectional data for street centerline files is very rare, and generally the databases to support this do not really exist. However, it is expected that as time progresses, more and more transportation asset information will be digitized.

Creating this many models in batch using procedural methods will likely require some amount of QAQC, and how much would depend on the complexity of the task.

These tools are still in development, and some of the bugs encountered were dealt with in ways that were not elegant (but they worked). Suggestions and thoughts are appreciated.

CityEngine Side: Once you map a streetWidth parameter to a street rule, to change the street width or sidewalk width you will need to change both the shape parameter AND the object attribute. Contact me for clarification on this point.
