# Create a custom CRS and Transform for Loading up a LCC-based Libyan Seismic cube

by Marcus Zou | 10 November 2022



## Business Needs

* A 3D Seismic cube of Concession NC-100 of west Libya has a projection of Lambert Conformal Conic ("LCC"), instead of the commonly used UTM Projection, and AGOCO-cooked Datum based on Clarke 1880 Ellipsoid. 

* Failed to load the seismic cube into Kingdom or Petrel due to lack of pre-defined Projected CRS related to that specific cube.

* Plan to create a Custom Projected CRS ("PCRS") and Transform for converting or loading up such seismic cube into Petrel sine Petrel software comes with a Coordinate System Manager, enabling us to cook that PCRS thing out.

* NC-100 Seismic cube - the parameters have been provided as is:

​		**AGOCO Lambert Datum Using 2 Parallels**

| Key                         | Value                        |
| --------------------------- | ---------------------------- |
| Ellipsoid                   | Clarke 1880                  |
| Projection                  | Lambert Conical Orthomorphic |
| Latitude of Origin          | $31\degree$ North            |
| Longitude of Origin         | $18\degree$ East             |
| Scale Factor @ the Origin   | 0.99938949                   |
| First Parallel              | $33\degree 00' 00''$         |
| Second Parallel             | $28\degree 59' 08.3''$       |
| False Northing              | 550,000m                     |
| False Easting               | 1,000,000m                   |
| Semi Major Axis             | 6,378,249.145m               |
| Reciprocal Flattening (1/f) | 296.465                      |
| Central Meridian            | $18\degree$                  |
| Zone                        | Libya North                  |



## Solutions Implemented



### Step 1 - Create a Custom Projected CRS conjuncted with a Geographic CRS

**Good WKT in one line for Libya-North-CL80-LCC-2SP (SOC-EXP 800002, Applied, refer to the relevant WKT file)**
PROJCS["Libya-North: Clarke-1880-LCC-2SP",GEOGCS["GCS_Nord_Sahara_1959",DATUM["D_Nord_Sahara_1959",SPHEROID["Clarke_1880_RGS",6378249.145,293.465]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433],AUTHORITY["EPSG",4307]],PROJECTION["Lambert_Conformal_Conic"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",550000.0],PARAMETER["Central_Meridian",18.0],PARAMETER["Standard_Parallel_1",33.0],PARAMETER["Standard_Parallel_2",28.985639],PARAMETER["Latitude_Of_Origin",31.0],UNIT["Meter",1.0],AUTHORITY["SOC-EXP",800002]]

**Good WKT in one line for Libya-North-CL80-LCC-1SP (SOC-EXP: 800001, to be Applied later, refer to the relevant WKT file)**
PROJCS["Libya-North: Clarke-1880-LCC-1SP",GEOGCS["GCS_Nord_Sahara_1959",DATUM["D_Nord_Sahara_1959",SPHEROID["Clarke_1880_RGS",6378249.145,293.465]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433],AUTHORITY["EPSG",4307]],PROJECTION["Lambert_Conformal_Conic"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",550000.0],PARAMETER["Central_Meridian",18.0],PARAMETER["Scale_Factor",0.99938949],PARAMETER["Latitude_Of_Origin",31.0],UNIT["Meter",1.0],AUTHORITY["SOC-EXP",800001]]




### Step 2 - Create a new Transform or borrow a in-situ Transform from Petrel

**GEOGTRANS: 3-Params (Borrowed from Petrel Catalog Library - EPSG Code: 1253)**
GEOGTRAN["Nord_Sahara_1959_To_WGS_1984",GEOGCS["GCS_Nord_Sahara_1959",DATUM["D_Nord_Sahara_1959",SPHEROID["Clarke_1880_RGS",6378249.145,293.465]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],GEOGCS["GCS_WGS_1984",DATUM["D_WGS_1984",SPHEROID["WGS_1984",6378137.0,298.257223563]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],METHOD["Geocentric_Translation"],PARAMETER["X_Axis_Translation",-186.0],PARAMETER["Y_Axis_Translation",-93.0],PARAMETER["Z_Axis_Translation",310.0],AUTHORITY["EPSG",1253]]

**GEOGTRANS: 7-Params (Borrowed from Petrel Catalog Library EPSG Code: 8562)**
GEOGTRAN["Nord_Sahara_1959_To_WGS_1984_3",GEOGCS["GCS_Nord_Sahara_1959",DATUM["D_Nord_Sahara_1959",SPHEROID["Clarke_1880_RGS",6378249.145,293.465]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],GEOGCS["GCS_WGS_1984",DATUM["D_WGS_1984",SPHEROID["WGS_1984",6378137.0,298.257223563]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],METHOD["Position_Vector"],PARAMETER["X_Axis_Translation",-156.0],PARAMETER["Y_Axis_Translation",-87.2],PARAMETER["Z_Axis_Translation",287.8],PARAMETER["X_Axis_Rotation",0.0],PARAMETER["Y_Axis_Rotation",0.0],PARAMETER["Z_Axis_Rotation",0.814],PARAMETER["Scale_Difference",-0.38],AUTHORITY["EPSG",8562]]




### Step 3 - Create a Conflation Policy (displayed as Coordinate System in Petrel)

 Conflation Policy (SOC-EXP Code: 750001) = CRS#**800002** + GEOGTRANS#**1253**
 Conflation Policy (SOC-EXP Code: 750002) = CRS#**800002** + GEOGTRANS#**8562**



### Step 4 - Load up the newly created CRS in Petrel

Refer to the attached PDF please.



### Step 5 - Share out the custom Geodetic Catalog to the peers

Refer to the attached PDF please.



## The End
