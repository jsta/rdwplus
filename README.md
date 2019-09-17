---
output: 
  html_document:
    keep_md: true
---



# rdwplus

An open source implementation of IDW-PLUS (inverse distance weighted percent land use for streams) from Peterson &amp; Pearse (2017). IDW-PLUS itself is a toolset that calculates the spatially explicit landscape representation metrics previously developed and used in Peterson et al. (2011). It is a Python-based ArcGIS toolbox, originally developed for ArcGIS version 10.3.1. This fully open-source implementation uses R as the scripting language, with calls to modules and tools from GRASS GIS (GRASS Development Team, 2019) to do the heavy lifting. 

## Installation

At present, `rdwplus` is available on GitHub only. Install the package `rdwplus` by using the command `devtools::install_github("apear9/rdwplus")`. Note that the package `devtools` must be installed in order for this command to run. 

Note that `rdwplus` calls GRASS GIS, so the user may also have to install GRASS GIS. The software is available at https://grass.osgeo.org/download/ or, for Windows users, as part of the OSGeo4W bundle at https://trac.osgeo.org/osgeo4w/.

## Using rdwplus

Load `rdwplus` after it has been installed. 

```
library(rdwplus)
```

Set up a GRASS session.

## Setting up a GRASS session

A GRASS session can very easily be set up through R. First, the user must find a folder containing their installation of GRASS GIS. If the user does not know where this folder is located, they can search for it by running

```
#  Note this may yield more than one directory, hence the [1]
my_grass <- search_for_grass()[1]
```

Once the location of the user's GRASS installation is known, the function `initGRASS` can be called to set up the GRASS session.

```
initGRASS(my_grass)
```

At this stage it is possible to set other environment parameters but, for this demonstration, the above is fine.

Now we can check that a GRASS session is running.

```
check_running()
```

We can then set up the GRASS environment. This means setting the extent, spatial resolution, coordinate system, etc., of the current GRASS mapset. This is done by giving the function `set_envir()` a file path to a raster file. 

```
set_envir()
```

## Data preprocessing

## Compute watershed attributes

## References

GRASS Development Team. (2019). Geographic Resources Analysis Support System (GRASS) Software, Version 7.6. Open Source Geospatial Foundation. https://grass.osgeo.org

Peterson, E.E. and Pearse, A.R. (2017). IDW-PLUS: an ArcGIS toolset for calculating spatially explicit watershed attributes for survey sites. *Journal of the American Water Resources Association*, *53*(5), 1241-1249. doi: 10.1111/1752-1688.12558

Peterson, E.E., Sheldon, F., Darnell, R., Bunn, S.E. and Harch, B.D. (2011). A comparison of spatially explicit landscape representation methods and their relationship to stream condition. *Freshwater Biology*, *56*(3), 590-610. doi: 10.1111/j.1365-2427.2010.02507.x.
