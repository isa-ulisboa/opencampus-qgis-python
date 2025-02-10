# qgis-python

[QGIS with Python: Open Campus course at ISA/ULisboa](https://www.isa-opencampus.pt/qgis-com-python), 4th Edition

Instructor: Manuel Campagnolo

Start: Wednesday, April 23, 2025, 6pm, online. In total, 10 sessions Mondays and Wednesdays 6-8pm until May 26, 2025.

## Main resources for the course 
* [Zoom link](https://videoconf-colibri.zoom.us/j/98394607195)
* [Fenix: class recordings and evaluation](https://fenix.isa.ulisboa.pt/courses/qwp-846413499991001)
* [Shared folder: data for exercises](https://ulisboa-my.sharepoint.com/:f:/r/personal/mlc_office365_ulisboa_pt/Documents/Documents/Aulas-Cursos/cursos_curta_duracao/qgis_com_python_2023/shared_folder?csf=1&web=1&e=1TeeOe)
* [GitHub site, with access to python scripts and searchable](https://github.com/isa-ulisboa/qgis-python)
* [Youtube channel](https://www.youtube.com/@qgisiwthpython)
* [Overview of topics and exercises](overview_pyqgis_geopandas_rasterio_2025.pdf)
* [PyQGIS Developer Cookbook](https://docs.qgis.org/3.34/en/docs/pyqgis_developer_cookbook/index.html) 

## QGIS instalation:
<details markdown="block">

  <summary> Links for download</summary>
  
*  **Windows**: Follow instructions for [installing QGIS via the OSGeo4W distribution manager](https://www.e-education.psu.edu/geog489/node/2294). You can also follow the video [install QGIS via OSGeo4W](https://www.youtube.com/watch?v=jtHnqvfa6is).
*  **MacOS**: Follow instructions from [Download QGIS](https://www.qgis.org/en/site/forusers/download.html)

</details>

<details markdown="block">
  
<summary> Step-by-step instructions for OSGeo4W (Windows)</summary>

Below are included step-by-step instruction for installing QGIS through OSGeo4W (Windows) and using OSGeo4W shell to install Python packages:
1. Downloading and installing QGIS (instructions for installing QGIS via the OSGeo4W distribution manager). [geog489](https://www.e-education.psu.edu/geog489/node/2294)
  - 1st: go to [download](https://qgis.org/en/site/forusers/download.html) and download OSGeo4W Network installer (Window users)
  - 2nd: execute the downloaded file `osgeo4w-setup.exe` (follow instructions in [https://www.e-education.psu.edu/geog489/node/2294](https://www.e-education.psu.edu/geog489/node/2294)): this will take some time. Files will be typically installed in `C:\OSGeo4W`. Note: to uninstall OSGeo4W, run `osgeo4w-setup.exe` and choose advanced installation and choose the packages you want to uninstall (can choose all). Then delete OSGeo4W folder.
  - Important files that are created during installation:
    - `C:\OSGeo4W\OSGeo4W.bat` - This opens the OSGeo4W shell that can be used for executing python scripts from the command line.
    - `C:\OSGeo4W\bin\qgis-ltr-bin.exe` - This is the main QGIS executable that you need to run for starting QGIS 3.
    - Obs: we will execute scripts directly in QGIS, so the OSGeo4W shell (windows key+ OSGeo4W shell) will only be needed to install Python packages (see below).
2. Installing a Python package that is not available in `C:\OSGeo4W\apps\Python3xx\Lib\site-packages`: execute `C:\OSGeo4W\bin\osgeo4w-setup.exe`; select *advanced mode*; follow menus; use search box to select package (say, `sklearn`) and chose *install*. The OSGeo4W setup can also be used to update or delete packages. 

</details>

## Sessions

Each topic (or task) *Txx* listed below corresponds to a folder that can be downloaded from this [Shared folder](https://ulisboa-my.sharepoint.com/:f:/g/personal/mlc_office365_ulisboa_pt/ElM7jQ_b__lEkznQ6mVRuhsBESim1iSIdK0v_7kXgvHw6A?e=UFWqMh). 

<details markdown="block">

  <summary>Session 1: Introduction; Python Console and editor in QGIS; Processing/History; processing.run(); STOPvespa dataset</summary>
  
  - Introduction to PyQGIS
  - T01: this first exercise uses two vector datasets, one that is loaded from a `shapefile` that represents Portuguese counties, and a point dataset (STOPvespa of locations of Asian hornet nests) that is read from a `csv` file. The goal is to load and visualize the data, and create a QGIS project "by hand"; Create the first script in Python to perform some simple operations: `extract by expression` and `extract by location`. To do this, one first execute the operations with tools in Processing/Toolbox, and then use Processing/History to copy the respective commands to the Python editor in the appropriate order. This is described in the first playlist in the [@qgisiwthpython Youtube channel](https://www.youtube.com/@qgisiwthpython).

</details>

<details markdown="block">
<summary>Session 2: Access to layers; Access to project and canvas; Zoom to layer; Use pathlib for paths and file names</summary>

  - T02: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. The goal is to access the QGIS project programmatically with PyQGIS. The script includes code to access and read a project, access the QGIS canvas, set the project coordinate reference system, list layers in canvas or project, refresh canvas, access a layer by name, change the layer name, extract the extent of a layer, zoom to layer, read the layer's id, access the `layerTreeRoot` and the available `QgsLayerTreeLayer`, and toggle layer visibility.
  - T03: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. The ultimate goal is to be able to change the orders of layer in the *Layers panel* programatically with PyQGIS. To do this, one needs to access the `QgsLayerTree` instance (root) and then, access and individual layer with a `QgsLayerTreeLayer` object. Finally, one needs to be able to clone, insert and remove object of class `QgsLayerTreeLayer` in the root. It is shown how to save changes in the project with action `mActionSaveProject`. The script also show how to create a second canvas in QGIS.
  - T05: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. The script shows how to export a QGIS vector layer as shapefile.
  - T06: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. The goal is to improve T02 in order to use paths relative to the project file location, use memory layers for intermediate results, save the final layer as file, use a variable (D) that defines the diameter threshold for the problem of determining the counties where nests larger than D occur. Module `Path` from package `pathlib` is used to manage paths and file names.

</details>

<details markdown="block">
  <summary>Session 3: Define functions and make Python code modular; Loops and conditionals; matplotlib </summary>

  - T07: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. The goal is to define functions and make code in T06  more compact and modular.
  - T08: It is assumed that the project `stopvespa.qgz` is loaded in QGIS before running the script. Again, it is explored how to define functions and make the script more modular. Create a separate file `my_functions.py` to store functons and load that file from the script. Simplify the code for the STOPvespa problem and organize the script by defining the main chunk of code with `def main():` and then calling it with `main()`. Create a loop over wasp nest diameters and plot results with Python package `matplotlib`. 
  
</details>

<details markdown="block">
  <summary>Session 4: Load layers with PyQGIS from shapefile and from csv file; create and update QGIS project; edit attribute table; CAOP+INE milk production dataset</summary>
  
  - T04: The goals of this script are creating and saving a new project. The script reads a shapefile as QGIS vector layer, changes the layer encoding, and reads a `csv` file as a text delimited QGIS layer.
  - T09: The goals are the same as T04, but with different data sets, and a more compact code. The new data set includes the location of Portuguese counties (CAOP) and a table of  Milk production per county from INE. In this case the csv file does not have coordinates while the one in T04 has. Therefore, the parameters for reading the `csv` file are different in T04 and T09.
  - T10: Extend T09 to `edit` and `join` attribute tables with PyQGIS. Namely, the script shows how PyQGIS can be used to edit the attribute table with `QgsField` and `addAttribute`. Check with `dataProvider().capabilitiesString()` if the attribute table can be edited. Access features and attributes with `getFeatures()`.
    
</details>

<details markdown="block">
  <summary>Session 5: Join tables;  Symbology for vector layers: single symbol and categorized symbol</summary>
  
  - T11: The data sets are again CAOP and a milk production table. The script shows how to join tables with `native:joinattributestable` to pass the values of milk production to the attribute table of the spatial dataset CAOP.
  - The appearance of the layer is given by `layer.renderer()`: this includes symbols associated to the layer. Symbols are classes which take care of drawing of visual representation of features, while renderers determine what symbol will be used for a particular feature. Symbols are generated from classes `QgsMarkerSymbol`, `QgsLineSymbol` and `QgsFillSymbol` depending on the geometry of the feature. See the following table for the combinations of geometries and types for single, categorized and graduated renderers [geometry vs type](vector_layers_symbols.png).
  - T12: The CAOP data set is rendered with `QgsSingleSymbolRenderer`. The script shows how to change vector layer symbology -- color, transparency, stoke_width, etc -- for single symbols.
  - T13: The goal is to change the legend to show which are the counties that produce milk and the ones that don't. In order to do this, one need to create a new categorical variable that gives that information. This is done by creating a new attribute with `QgsField` and  `addAttribute`. Then, the values for the new attribute are computed by visiting the attribute table with `getFeatures()`.
  - T14 is the continuation of T13 and focus on the creation of the renderer to change the layer's symbology. It is created with `QgsCategorizedSymbolRenderer` and uses the new categorized variable defined in T13. 
  
</details>

<details markdown="block">
  <summary>Session 6: Categorized and graduated symbols; using dictionaries and functions to create vector layer renderers</summary>
  
  - T15, an improvement of T14. A dictionary is created to hold the categories for the renderer. Therefore, one can create a dictionary with an arbitrary number of categories and call a function to convert that dictionary into a renderer to change the layer's legend.
  - T16: Graduated symbols. In this example, we use a color ramp similarly to what is done "by hand" in QGIS. One can choose the color ramp, the number of classes and the classification method as in the symbology interface for graduated symbols. The code to define the  renderer is encapsulated in a function.
  - T17, an improvement of T16: since the INE milk production data set includes different types of milk, this scripts contains PyQt5 widgets to interact with the user so the user can choose which type of milk to use for the legend. `QInputDialog.getItem` is used to create a drop-down menu; `QMessageBox.question` is used to ask a yes/no question and store the answer; `QMessageBox.information`is used to convey information to the user through message boxes in QGIS.
  - T18:  Graduated symbols again, but this time a dictionary is created to hold each range of values of the attribute, the labels, etc, making the renderer more flexible than in T16.
  - T19: Graduated symbols still as in T18, but now, instead of creating a dictionary from scratch, there is a function that creates the dictionary. In this example, the function creates a dictionary with N ranges, where N is given by Sturges rule, and the symbol for each range is defined from a given colormap, with a formatted label. This approach provides increased flexibility in creating a graduated symbology.
  
</details>

<details markdown="block">
  <summary>Session 7: Raster datasets (geotiff files); load with PyQGIS; set nodata value; package rasterio; symbology </summary>
  
  - T20: Read single band geotiff file (DEM) with `iface.addRasterLayer`; Extract information about layer (width, height, extent, nodata value); Set nodata value for layer; Contrast enhancement.
  - T21: As an alternative to using PYQGIS as in T20, the raster file can be opened and processed with Python package `rasterio`; Create histogram; Set nodata value with rasterio; Export raster with rasterio; Note that there is no direct way to convert a rasterio raster object into a QGIS raster layer.
  - T22: This is a continuation of T20 with the same DEM dataset; Instead of creating a gray symbology (default), one can create a `QgsSingleBandPseudoColorRenderer` and render the raster with colors.
  - T23: The input is a multiband raster (Sentinel 2 image with four 10 m resolution spectral bands); Load file and create a raster layer; Compute band statistics with PyQGIS;  Create color composites with PyQGIS and contrast enhancement (e.g. mean +/- standard error range)
  
</details>


<details markdown="block">
  <summary>Session 8: Processing raster datasets (geotiff files) with PyQGIS; Exporting a raster layer to file; Combining raster and vector processing to determine solar panels plant locations from Sentinel-2 imagery; Rasterio geoprocessing tools</summary>
  
  - T24: Clip raster (Sentinel-2 multiband image) by vector layer (county Alcoutim extracted from CAOP) with `gdal:cliprasterbymasklayer` (see two first operations in [this diagram](diagram_exercise_alcoutim.pdf)); Save raster layer as geotiff file with PyQGIS `QgsRasterFileWriter`.
  - T25: Consider the problem of determining the location of solar panels by analyzing Sentinel-2 10 m imagery with PyQGIS; Create script in PyQGIS to implement the sequence of steps in [this diagram](diagram_exercise_alcoutim.pdf) and obtain a vector layer with the approximate extension of industrial solar panels.
  - T25B: In this script, it is illustrated how some of the geoprocessing steps in T25 can be done with rasterio instead of PyQGIS. Arithmetic and logical operations can be applied directly, in a more straightforward manner than `raster calculator` in PyQGIS; Apply a seive to a raster with `rasterio.features.sieve`; Export rasterio to `tif` with `rasterio.open` in writing mode.
  
</details>


<details markdown="block">
  <summary>Session 9: Rasterio; Geopandas example; Convert Geopandas dataframe to vector layer with json; Merge tables with Pandas and Geopandas; Export Geopandas as shapefile</summary>
  
  - T26: Package **Geopandas** is an extension of the widely used **Pandas** package for data frames (tables). Geopandas tables have a special column called **geometry** that stores the geometry of the respective feature. With this short example, it is shown how to read a shapefile with Geopandas, how to perform simple manipulation of the data and do some geoprocessing (e.g. replace feature geometry by a same extension rectangle with `gdf.geometry.envelope`), and how to convert  a Geopandas dataframe with `gdf.to_json()` into a QGIS vector layer for easy visualization and further processing in QGIS.
  - T27: The goal of the exercise is to join by attributes a shapefile of counties and a table of wine production from each county. This could be done as in T11 with PyQGIS using tool `native:joinattributestable`. Here, instead, the shapefile and the tables are read with Pandas and Geopandas, and the tables are preprocessed with Pandas and merged with `merge`. Finally, the resulting merged table with geometries and wine production values is exported to a *shapefile* using Geopandas.

</details>

<details markdown="block">
  <summary>Session 10: Use Python to create a common legend for yearly maps; Access Layout manager with PyQGIS and export maps as pdf or png</summary>

  - T28: The goal of the exercise is to create a common legend for the wine production for all available years. The distribution of production values is very skewed so equal class intervals are not ideal. It would be easy to create a separate legend for each year as in T19 which uses Jenks to define the ranges of N classes for a graduated symbology. However, the legends for the different years would not be comparable since ranges would be different. In this example, a common symbology is created for all years. This is done by reading the data with Geopandas, and using Python `Jenkspy` package to compute the Jenks breaks and create a unique dictionary of ranges for the wine production values of all years.  That dictionary is then used to create the graduated symbology renderer for the vector layer in QGIS that represents the production for each  specific year. To help visualizing the evolution of wine production along the years, the script also turns on/off the visibility of each layer as in T02.
  - T29: This script re-uses a large part of the code from T28 but creates the legend for a single year. The goal is to create automatically map outputs in format `pdf` or `png` with map, legend, scale bar and title. This can be easily generalized to create a file per year, with all maps sharing the same legend. The script shows how PyQGIS has access to the QGIS Layout Manager.

</details>


## Short useful blocks of PyQGIS code

<details markdown="block">
  <summary>Simple code to load vector (e.g. shapefile) and raster (e.g. geotiff) files as layers and export vector and raster layers as files </summary>

  - Create empty project:
    ```
    QgsProject.instance().clear()
    ```
  - Load shapefile as QGIS vector layer:
    ```
    # fn is the path to the file (e.g. with extension .shp)
    mylayer=iface.addVectorLayer(str(fn),'layer_name','ogr')
    ```
  - Load shapefile as *memory* QGIS vector layer:
    ```
    # fn is the path to the file (e.g. with extension .shp)
    mylayer=QgsVectorLayer(str(fn),"", "ogr")
    mylayer.selectAll()
    clone_layer = processing.run("native:saveselectedfeatures", {'INPUT': mylayer, 'OUTPUT': 'memory:'})['OUTPUT']
    mylayer.removeSelection()
    clone_layer.setName('layer_name')
    QgsProject().instance().addMapLayer(clone_layer)
    ```
  - Load geotiff as QGIS raster layer:
    ```
    # fn is the path to the file (e.g. with extension .tif)
    mylayer=iface.addRasterLayer(fn,'layer_name','gdal')
    ```
  - Load openstreetmaps (OSM) as QGIS raster layer:
    ```
    uri_OSM = 'type=xyz&url=https://tile.openstreetmap.org/{z}/{x}/{y}.png&zmax=19&zmin=0'
    iface.addRasterLayer(uri_OSM, "OpenStreetMap", "wms")
    ```
  - Save QGIS vector layer as shapefile:
    ```
    # fn is the path to the output file (e.g. with extension .shp)
    processing.run("native:savefeatures", {'INPUT':mylayer, 'OUTPUT':fn})
    ```
  - Save QGIS vector layer as shapefile (2nd alternative):
    ```
    # fn is the path to the output file (e.g. with extension .shp)
    # Driver name and encoding
    options = QgsVectorFileWriter.SaveVectorOptions()
    options.driverName = 'ESRI Shapefile'
    options.fileEncoding = 'UTF-8'
    # instance of QgsCoordinateTransformContext
    context = QgsProject.instance().transformContext()
    # write to file
    QgsVectorFileWriter.writeAsVectorFormatV3(mylayer, fn, context,options)
    ```
  - Export QGIS raster layer as geotiff:
    ```
    # fn is the path to the output file (e.g. with extension .tif)
    pipe = QgsRasterPipe()
    pipe.set(mylayer.dataProvider().clone())
    file_writer = QgsRasterFileWriter(str(fn))
    file_writer.writeRaster(pipe, mylayer.width(), mylayer.height(), mylayer.extent(), mylayer.crs())
    ```
  - Convert geopandas dataframe to QGIS vector layer:
    ```
    # gdf is a geopandas dataframe
    mylayer = QgsVectorLayer(gdf.to_json(),'layer_name',"ogr")
    QgsProject.instance().addMapLayer(mylayer)
    ```

</details>


<details markdown="block">
  <summary>Project, canvas, manipulate layers and paths</summary>

  Below, **it is supposed that there is already a project loaded in QGIS with vector layers**. The scripts below allow to manipulate those layers, zoom to layer, remove layers from the project, etc.

  - Function that returns the path to the current project:
    ```
    def my_project_path(my_project):
        """
            output: Path to the folder where the project is
        """
        # If there is a project, mufolder will be location of the project
        if my_project.fileName()!='':
            print('project', Path(my_project.fileName()).stem ,  'loaded')
            return Path(my_project.homePath())
        else:
            print('No project available')
            return 0 # exits main if there is no project available
    ```
    
  - Function that returns a layer which name matches a layer in the current project:
    ```
    def my_find_layer(ln):
        """
            tries to find a project layer which name is ln
        """
        layers=QgsProject().instance().mapLayersByName(ln)
        if len(layers)>1:
            print('Warning: there is more than one layer with name',ln)
            return layers[0]
        if len(layers)==1:
            return layers[0]
        print('Warning: no matches for', ln)
        return None
    ```
  - Function that finds a layer which name contains the string "approx_ln":
    ```
    def my_find_approx_layer(approx_ln):
        """
            tries to find a layer which name includes approx_ln
        """
        layers=QgsProject().instance().mapLayers().values() # dictionairy of all layers
        for layer in layers:
            ln=layer.name()
            if approx_ln in ln: # True if the layer name contains approx_ln
                return my_find_layer(ln)
        return None # in case no match is found
    ```
  - Function to zoom to the layer which name is layer_name:
    ```
    def my_zoom_to_layer(layer_name):
        """
            input: layer name
            works if the project crs is compatible with extent of the input layer
        """
        # Access layer in project if it exists
        mylayers=QgsProject().instance().mapLayersByName(layer_name)
        # mylayer is the first in the returned list
        if mylayers:
            mylayer=mylayers[0]
            # setproject CRS so it is the same as mylayer.crs()
            QgsProject.instance().setCrs(mylayer.crs())
            # Determine extent
            extent = mylayer.extent()
            iface.mapCanvas().setExtent(extent) 
            iface.mapCanvas().refresh()
    ```
  - Function that removes a layer from the project:
    ```
    def my_remove_layer(layer):
        """
            removes layer from project
        """
        if layer in QgsProject().instance().mapLayers().values():
            QgsProject().instance().removeMapLayer(layer.id())
    ```
</details>

<details markdown="block">
  <summary>Create new project, load vector layers and delimited text files, process layers with processing.run() and save output to file</summary>

  Functions below allow to process layers with `processing.run` and execute tools from QGIS processing toolbox. The best pratice while processing data consists in creating temporary layers until the final reult is obtained. Then, the final layer can be exported as a file (e.g. *shapefile*).
  - Function that creates an empty project, with a name and saves it to a qgz file:
    ```
    def my_create_project(my_folder,project_name):
        """
            Create new project, set title, and save
        """
        my_project=QgsProject.instance() # QgsProject
        my_project.clear() # Clear project 
        my_project.setTitle(project_name)
        project_file=str(my_folder/project_name)+'.qgz'
        # Save project to file
        my_project.write(project_file) # 
    ```
  - Function that reads a vector file, and adds to the project a clone of that file as a 'memory' layer:
    ```
    def my_add_to_memory_vector_layer_from_shapefile(fn,ln):
        """
             add and name vector layer from file
             fn: string: path_to_file
             ln: string: output layer name
             output: layer copied to memory layer
        """
        mylayer=QgsVectorLayer(str(fn),"", "ogr")
        mylayer.selectAll()
        clone_layer = processing.run("native:saveselectedfeatures", {'INPUT': mylayer, 'OUTPUT': 'memory:'})['OUTPUT']
        mylayer.removeSelection()
        clone_layer.setName(ln)
        QgsProject().instance().addMapLayer(clone_layer)
        return clone_layer
    ```
  - Function that reads a delimited text file (e.g. csv or txt), sets encoding to 'utf-8' and adds it as a layer to the project:
    ```
    def my_add_layer_from_csv(fn,ln,params):
        """
            reads csv file and adds to project
        """
        # create uri as string
        uri=fn.as_uri()+params
        # create and load layer
        mylayer = QgsVectorLayer(uri, '' , "delimitedtext")
        # encoding
        provider=mylayer.dataProvider()
        if provider.encoding()!='UTF-8':
            mylayer.dataProvider().setEncoding('UTF-8')
        # set name
        mylayer.setName(ln)
        # add to project
        QgsProject().instance().addMapLayer(mylayer)
        return mylayer
    ```
    An example of a call to this function (T11):
    ```
    params_ine='?delimiter=;&detectTypes=yes&geomType=none'
    ine=my_add_layer_from_csv(fn,'INE',params_ine)
    ```
  - Function that executes QGIS tool from processing toolbox with *processing.run*:
    ```
    def my_processing_run(operation,ln_input,dict_params,layer_name):
        """ 
            function to execute processing.run from a list of parameters
            it creates a temporary output (in memory)
            ln_input is either the input layer or the name (a string) of the input layer
            dict_params: dictionary with operation parameters except 'INPUT' and 'OUTPUT'
            layer_name: name for the output layer
            output: output QgsVectorLayer
        """
        dict_params['INPUT']=ln_input
        dict_params['OUTPUT']=QgsProcessing.TEMPORARY_OUTPUT
        mylayer=processing.run(operation,dict_params)['OUTPUT']
        mylayer.setName(layer_name)
        QgsProject().instance().addMapLayer(mylayer)
        return mylayer
    ```
    Example of a call to this function (T08):
    ```
    params={'PREDICATE':[1], 'INTERSECT':vespa_D}
    conc_D=my_processing_run("native:extractbylocation", caop, params, ln)
    ```
  - Function that exports a temporary layer to a file (e.g. a *shapefile*):
    ```
    def my_export_layer_as_file(vlayer,fn):
        """ 
            inputs: vector layer and path to output file
        """
        if isinstance(vlayer,QgsVectorLayer):
            # file path is converted into a string
            processing.run("native:savefeatures", {'INPUT':vlayer, 'OUTPUT':str(fn)})
    ```
</details>

<details markdown="block">
  <summary>Edit attribute table, add new attribute, compute attribute values</summary>

  Often, we need to make changes on vector layers in QGIS. Vector layers have attributes (aka fields) that correspond to the *columns* of the layer's **attribute table**. There is one special field which is the **geometry** and contains the geometry of each feature of the layer. The features correspond to the *rows* of the attribute table. Each feature has therefore a geometry (unless the layer is just a non spatial regular table) and has values for all attributes. 
  
  PyQGIS provides methods to add new attributes to the attribute table with `layer.addAttribute(fld)` where `fld` is an object of class `QgsField`. It also provides a method to delete attributes, with `layer.deleteAttribute(index_of_the_field)`. After changes are made, the layer needs to be updated with `layer.updateFields()`.
  
   To iterate over all features from a layer, on can use the *for loop* `for feat in layer.getFeatures():`. Then, the value of some attribute is accessible with `feat[attribute_name]`. One can also add a new feature to the attribute table with `layer.addFeature(feat)` where `feat` is an object of class `QgsFeature`, or remove a feature with `layer.deleteFeature(id_of_the_feature)`. The geometry of some feature can be set or changed with `feat.setGeometry(geom)`or `layer.changeGeometry(id_of_the_feature,geom)`, where `geom`is an object of class `QgsGeometry`. After changes are made, the feature needs to be updated with `layer.updateFeature(feat)`.
  
  - Function that edits a vector layer and computes the values of one field as a function of the values of the other field (T10):
    ```
    def my_INE_preprocessing(layer):
        """
        Edits the vector layer and make some changes to it
        The goal is to compute the values of attribute di_co from the values of attribute NUTS_2013
        Only the values of NUTS_2013 with maximum length are of interest (those are the counties)
        """
        # 1st: determine maximum length of NUTS_2013
        maxDigits=0
        for feat in layer.getFeatures():
            if len(feat['NUTS_2013']) > maxDigits:
               maxDigits=len(feat['NUTS_2013'])
        
        # 2nd: for those, compute and store new 4-digit code (last 4 digits) in di_co
        with edit(layer):
            for feat in layer.getFeatures():
                if len(feat['NUTS_2013']) == maxDigits:
                    feat['di_co'] = feat['NUTS_2013'][-4:] # last 4 digits
                    # “update-after-change”
                    res=layer.updateFeature(feat) # 'res' to be silent
        # return output layer
        return layer
    ``` 
  - Function that adds a field to a layer and computes the values for that field as a function of the values of an existing field (T13):
    ```
    def my_add_string_attribute_and_compute_value(layer):
        '''
        input: layer
        creates a new field called 'produces' and computes its values from the values of an existing field 'Total'
        '''
        # Create new categorized attribute 'produces' with values 'yes' or 'no'
        fld=QgsField('produces',QVariant.String)
        with edit(layer):
            layer.addAttribute(fld) 
            layer.updateFields()
            for feat in layer.getFeatures():
                if feat['Total'] == 0:
                    feat['produces'] = 'no' 
                else:
                    feat['produces'] = 'yes' 
                # “update-after-change”
                layer.updateFeature(feat) # 'res' to be silent
                return layer
    ```
</details>

<details markdown="block">
  <summary>Symbology for vector and raster datasets</summary>

  - Function that creates a categorized legend for a vector layer from a dictionary; and function that creates a dictionary 
    ```
    def create_categorized_legend(vlayer,attrib,dict):
        '''
        input: 
        1.layer to render, 
        2. string: attribute to use, 
        3. dictionary for the legend where the key is the value the attribute takes, and the values are the class label (a string), the color (QColor object), and the opacity (float)
        no output
        '''
        # create categories from mydict
        categories=[] # empty list
        for myvalue, (mylabel,myQcolor, myopacity) in dict.items():
            mysymbol=QgsSymbol.defaultSymbol(vlayer.geometryType())
            mysymbol.setColor(myQcolor)
            mysymbol.setOpacity(myopacity)
            cat=QgsRendererCategory(myvalue, mysymbol, mylabel)
            categories.append(cat)
        # create renderer
        renderer = QgsCategorizedSymbolRenderer(attrib, categories)
        vlayer.setRenderer(renderer)
        # Refresh layer
        vlayer.triggerRepaint()
    ```
    Below, is a example of a function that creates a dictionary of random colors.
    ```
    def create_random_categorized_dict(myListValues,colorMin=0,colorMax=255,opacity=1):
        '''
        function that creates dictionary from list of values
        myListValues is a list of values: each value corresponds to an item of the dictionary
        '''
        import random
        myDict={} # initialize
        # creates dictionary: one entry per value in myListValues
        for val in myListValues:
            val = str(val) # to be sure it is a string
            myR=random.randint(colorMin,colorMax) 
            myG=random.randint(colorMin,colorMax)
            myB=random.randint(colorMin,colorMax)
            myQColor=QColor(myR,myG,myB)
            # insert a new entry to the dictionary
            myDict.update({val : (val,myQColor,opacity)})
        return myDict
    ```
    The list `myListValues`could for instance be determined from the layer and the attribute that is used to create the legend.
    ```
    idx = mylayer.fields().indexOf(attribute_name)
    myListValues = list(mylayer.uniqueValues(idx)) # need to be converted in list since uniqueValues returns a "set"
    ```
- Function that creates a symbology for a single band raster layer.

    ```
    def create_raster_ramp_legend(lyr,dict, type='Linear'):
        ''' 
        legend for raster 
        type is 'Linear' (interpolated ramp, by default), 'Discrete', 'Exact',...
        inputs: layer and dictionary with label: (color, limit)
        '''
        s = QgsRasterShader()
        # Instantiate the specialized ramp shader object:
        c = QgsColorRampShader()
        # Name a type for the ramp shader. 
        if (type=='Linear'): c.setColorRampType(QgsColorRampShader.Interpolated)
        if (type=='Discrete'): c.setColorRampType(QgsColorRampShader.Discrete)
        if (type=='Exact'): c.setColorRampType(QgsColorRampShader.Exact)
        # Create a list hold our color ramp definition:
        i = []
        # Populate the list with color ramp color values for each range:
        for label, (color, limit) in dict.items():
            i.append(QgsColorRampShader.ColorRampItem(limit, color, label)) 
        # Assign the color ramp to our shader:
        c.setColorRampItemList(i)
        # Tell the generic raster shader to use the color ramp:
        s.setRasterShaderFunction(c)
        #Next we create a raster renderer object with the shader:
        ps = QgsSingleBandPseudoColorRenderer(lyr.dataProvider(), 1, s)
        # Assign the renderer to the raster layer:
        lyr.setRenderer(ps)
        #Finally we add the layer to the canvas to view it:
        lyr.triggerRepaint()
        # Should not be necessary
        iface.layerTreeView().refreshLayerSymbology(lyr.id())
        return lyr
    ```
    The dictionary input for the function above could be something like the following:
    ```
      dict={
      'cluster1': (QColor('red'),0),
      'cluster2': (QColor('yellow'),1),
      'cluster3': (QColor('black'),2)
      }
    ```
</details>

## Some useful links
<details markdown="block">
  <summary> Documentation (QGIS, PyQGIS) </summary>

  * (main resource: tutorial and a reference guide) PyQGIS Developer Cookbook. [https://docs.qgis.org/3.28/en/docs/pyqgis_developer_cookbook/index.html](https://docs.qgis.org/3.28/en/docs/pyqgis_developer_cookbook/index.html) or [https://docs.qgis.org/testing/pdf/en/QGIS-testing-PyQGISDeveloperCookbook-en.pdf](https://docs.qgis.org/testing/pdf/en/QGIS-testing-PyQGISDeveloperCookbook-en.pdf)
  * Documentation for QGIS (also accessible through QGIS Python editor). [https://docs.qgis.org/3.28/en/docs/index.html](https://docs.qgis.org/3.28/en/docs/index.html)
  * QGIS Python API:  [https://qgis.org/pyqgis/master/core/index.html](https://qgis.org/pyqgis/master/core/index.html)

</details>

<details markdown="block">
  <summary> Introductory tutorials on PyQGIS </summary>
  
1. Broad range tutorials:
  * PyQGIS 101: Introduction to QGIS Python programming for non-programmers. [https://anitagraser.com/pyqgis-101-introduction-to-qgis-python-programming-for-non-programmers/](https://anitagraser.com/pyqgis-101-introduction-to-qgis-python-programming-for-non-programmers/)
  * Tutorial on QGIS 3 programming with Python (PyQGIS): [https://www.geodose.com/p/pyqgis.html](https://www.geodose.com/p/pyqgis.html)
  * QGIS Tutorials and Tips (with section on PyQGIS): [https://www.qgistutorials.com/en/index.html](https://www.qgistutorials.com/en/index.html)
  * Customizing QGIS with Python (Full Course Material) 3.16: [https://courses.spatialthoughts.com/pyqgis-in-a-day.html](https://courses.spatialthoughts.com/pyqgis-in-a-day.html)
  * QGIS Python course by Victor Olaya: [https://github.com/volaya/qgis-python-course](https://github.com/volaya/qgis-python-course)
  * Automating QGIS3 with Python: [https://www.udemy.com/course/automating-qgis-3xx-with-python/learn/lecture/15679972#overview](https://www.udemy.com/course/automating-qgis-3xx-with-python/learn/lecture/15679972#overview)
  * QGIS Python Tutorial (Open source options PyQGIS Tutorial): [https://www.youtube.com/watch?v=X-LvGvNor4E](https://www.youtube.com/watch?v=X-LvGvNor4E)
  * Course Unleash QGIS with Python, 2nd edition: [https://github.com/manuelcampagnolo/PyQGIS_2nd_edition](https://github.com/manuelcampagnolo/PyQGIS_2nd_edition)
  
2. More specific topics:
  * PyQGIS: Create and Print a Map Layout with Python: [https://opensourceoptions.com/pyqgis-create-and-print-a-map-layout-with-python/](https://opensourceoptions.com/pyqgis-create-and-print-a-map-layout-with-python/)
  * Symbolizing Vector and Raster Layers (2015): [https://www.gislounge.com/symbolizing-vector-and-raster-layers-qgis-python-programming-cookbook/](https://www.gislounge.com/symbolizing-vector-and-raster-layers-qgis-python-programming-cookbook/)
  * An Intro to the Earth Engine Python API [https://github.com/google/earthengine-community/blob/master/tutorials/intro-to-python-api/index.ipynb](https://github.com/google/earthengine-community/blob/master/tutorials/intro-to-python-api/index.ipynb)

</details>

<details markdown="block">
  <summary>  Tutorial on creating plugins in QGIS3 </summary>
  
* [https://www.qgistutorials.com/en/docs/3/building_a_python_plugin.html](https://www.qgistutorials.com/en/docs/3/building_a_python_plugin.html)
</details>

<details markdown="block"> 
  
  <summary> Geopackage and SQLite </summary>

* How to create and populate a geopackage in QGIS ([video](https://www.youtube.com/watch?v=rLLP7NImZsU))
* [Load geopackage layers with PyQGIS](https://anitagraser.com/pyqgis-101-introduction-to-qgis-python-programming-for-non-programmers/pyqgis-101-creating-functions-to-load-geopackage-layers/)
* [How do I do that in SpatialLite and SQLite](https://www.researchgate.net/profile/Arthur-Lembo/publication/313236676_How_do_I_do_that_in_SpatiaLiteSQLite_Illustrating_Classic_GIS_Tasks/links/5893493645851563f828e2de/How-do-I-do-that-in-SpatiaLite-SQLite-Illustrating-Classic-GIS-Tasks.pdf?_sg%5B0%5D=KV_noEuBaQYN_lsdLb8UHcCU0q0Qg1eb6XEsV_zS-EAJdcQ5lGHcDAp07kzuH8bY-ylR1EQmc_JzCwPeMFvO8w.sAO2zeigLecEIg79M9A8H-I8Xqnwkbd1eMEgq8M75MJIbEFy-VC2q_-NnURsSRpRZoxHXhXC8S1oj449J0l5Mw&_sg%5B1%5D=92xoHnfLzUsK1DLwsPzVTrFWy9wjdsZDvdkFL0Kcnur_fQCQSp09YG44puo5ezPLQdMA-M0KWKjbm34fx87kiuvNZ2r1nslGjaPYOxOWTbKJ.sAO2zeigLecEIg79M9A8H-I8Xqnwkbd1eMEgq8M75MJIbEFy-VC2q_-NnURsSRpRZoxHXhXC8S1oj449J0l5Mw&_iepl=) (many examples of spatial SQL queries)

</details>

<details markdown="block">
<summary> Geoprocessing with Python (not just with QGIS) </summary>
  
* Geocomputation with Python: [https://py.geocompx.org/](https://py.geocompx.org/). Note: if you have experience on geocomputation with R, check out [https://geocompx.org/](https://geocompx.org/) and the post [https://geocompx.org/post/2023/ogh23/](https://geocompx.org/post/2023/ogh23/) on "Geographic data analysis in R and Python: comparing code and outputs for vector data"
* [PyGIS - Open Source Spatial Programming & Remote Sensing](https://pygis.io/docs/a_intro.html); geowombat; geopandas; rasterio
* There are many available courses on geocomputation with Python, that explore the appropriate Python packages.
</details>

<details markdown="block">
<summary> Introduction to Python </summary>
  
* W3schools: [https://www.w3schools.com/python/exercise.asp](https://www.w3schools.com/python/exercise.asp)
* [Python Programming Beginner Tutorials by Corey Schafer](https://www.youtube.com/playlist?list=PL-osiE80TeTskrapNbzXhwoFUiLCjGgY7):

</details>

<details markdown="block">
<summary>GDAL</summary>
  
* An Introduction to GDAL: [https://www.youtube.com/watch?v=N_dmiQI1s24](https://www.youtube.com/watch?v=N_dmiQI1s24)
</details>
