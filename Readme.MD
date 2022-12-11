# Loading an Unusual Seismic Cube

by Marcus Zou | 24 November 2022



## Business Needs

* A 3D Seismic cube of Concession NC-100 of west Libya has a projection of Lambert Conformal Conic ("LCC"), instead of the commonly used UTM Projection, and AGOCO-cooked Datum based on Clarke 1880 Ellipsoid. 

* Failed to load the seismic cube into Kingdom or Petrel due to lack of pre-defined Projected CRS related to that specific cube.

* Plan to create a Custom Projected CRS ("PCRS") and Transform for converting or loading up such seismic cube into Petrel sine Petrel software comes with a Coordinate System Manager, enabling us to cook that PCRS thing out.

* NC-100 Seismic cube - the parameters have been provided as is.



## Solutions Implemented

1. [Understanding and Customizing Coordinate System - Rev2A - 23 Nov 2022](Understanding and Customizing Coordinate System - Rev2A_23Nov2022.pdf)
2. [Custom CRS in Kingdom 2021/2017 - Rev2A - 23 Nov 2022](Custom CRS in Kingdom 2021-2017 by Marcus Zou - Rev2A_23Nov2022.pdf)
3. [Custom CRS in Petrel 2018-2022 - Rev2A - 24 Nov 2022](Custom CRS in Petrel 2018-2022 by Marcus Zou - Rev2A_24Nov2022.pdf)



## WKT & JSON

* The attached WKT files can be used in any applications since they are in standard WKT format, but will not be shared.

* Study hard, then you will figure out how to make those WKT happen.

  1_GCS_AGOCO.WKT
  
  2_PCRS_Libya-North-CL80-LCC-2SP_SOC-EXP_800001.WKT
  
  2_PCRS_Libya-North-CL80-LCC-2SP_SOC-EXP_800002.WKT
  
  3_GEOGTRANS_3Params_EPSG_1253.WKT
  
  3_GEOGTRANS_7Params_EPSG_8562.WKT
  
  4_CONFLATION-POLICY_SOC-EXP_750001&750002.JSON
  
  5_AIO_PCRS-Libya-North-CL80-Lambert-Conical.JSON
  
  

## Credits

* EPSG - www.epsg.io

* ArcGIS - www.arcgis.com

* Blue Marble Geographics - www.bluemarblegeo.com

* Wikipedia - www.wikipedia.org

* Schlumberger Ltd.

* IHS-Markit (S&P Global)



