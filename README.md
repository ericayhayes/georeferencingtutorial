
## Programming Historian Tutorial on Georeferencing and Displaying Historical Maps with Map Warper and ArcGIS online
*By Erica Hayes and Mia Partlow*

# Lesson Goals

Georeferencing is the process of assigning geographic coordinates to a scanned map or raster image. Many historians are now georeferencing historical maps in order to study how places have changed over time. In this lesson, we will take you through the steps to align geographic coordinates to a scanned historical map and show you how to share your georeferenced map online using an interactive web-based mapping platform, ArcGIS Online. While you may have already encountered the *Programming Historian* tutorial on [Georeferencing in QGIS 2.0](https://programminghistorian.org/en/lessons/georeferencing-qgis), we wanted to provide you with some examples of other entry-level georeferencing tools.

Before you begin georeferencing a scanned map, it is important to understand the locations depicted on the map, as well as the context of the creation of the historic map itself. Not all historic maps are good candidates for georeferencing. There must be enough information on the map to allow you to confidently assign latitude and longitude coordinates to it or align it with a GIS map using physical features. Often, you will need to research the location of historic places and features that no longer exist, and make an informed decision in order to identify its proper placement. Some maps may not have enough geographic information, and may become so warped when georeferenced that they are illegible or inaccurate.

![](images/mapwarper_warped.png)
*Fig. 1: A map too warped to be use effectively*

The scale, resolution, and projection of a scanned map are also important considerations when choosing a historic map to georeference. Small scale maps are generally not well suited for highly detailed georeferencing and may cause problems with representing exact feature locations. When selecting or scanning a historic map for georeferencing, it is better to use a map that has been scanned at a high resolution (300 dpi or greater), so you can easily see the features on the map when zooming in and out. It is also best practice to use the same projection as the historic map in order to minimize distortion. Georeferencing a map in the wrong projection can create a mismatch between your historical and current maps, stretching the lines, shapes, and the distance between objects. Map Warper, the tool used in this tutorial, does not provide an option to re-project your map data; if you are unable to achieve a legible map, or if you are measuring distance, you may need to use a more advanced GIS software, such as QGIS or ArcGIS Pro, which will allow you to specify the map projections. For more details on best practices for georeferencing, see [Esri’s list of recommendations](https://www.esri.com/esri-news/arcuser/spring-2014/~/media/Files/Pdfs/news/arcuser/0314/seven-best-practices.pdf).

In this tutorial, you will work with Map Warper and ArcGIS Online to create a georeferenced historical map and overlay it on top of a modern basemap to be published and interacted with on the web. Developed by Tim Waters, [Map Warper](https://mapwarper.net) is an open-source georeferencing service, written in Ruby on Rails and lets users upload scanned maps and georeference them against OpenStreetMap. [ArcGIS Online](https://www.esri.com/en-us/arcgis/products/arcgis-online/overview) is a cloud-based mapping and web analysis platform by Esri. You can use ArcGIS Online to create maps, analyze data, tell stories, and share maps online.

# Getting Started: Georeferencing your map with Map Warper
*You will start by uploading a map and georeferencing it using the open source online tool Map Warper. Map Warper has a variety of export options, including WMS URL, Tiles, and a GeoTIFF or KML file. For the purposes of this tutorial we will export the georeferenced map as Tile layer and load it into to ArcGIS Online.*

## Step 1: Set up Map Warper and upload your map

1. For this tutorial, we will use an [1860 map of North Carolina and South Carolina](https://bit.ly/3464cFd) from the David Rumsey Map Collection. Export and download the Extra-Extra Large version.

  * Note: Every filename in Map Warper must be unique, so you will need to give the image a new file name once you have downloaded the map to your computer, such as NC_SC_Map_yourlastname.jpg.


2. Go to [https://mapwarper.net](https://mapwarper.net) and create an account.


3. On the Home page, click the green button labeled Upload Map to import your scanned map to Map Warper.


4. The next screen is asking for descriptive information that will make the map easier to find (also known as metadata). While only the Title field is required, it is generally best practice to provide as much information as possible, so other users can learn more about the source of your scanned map you are georeferencing. Fill in the metadata based on the information provided to you about the historical map that you’re working with. For the North Carolina and South Carolina map, you can find the map’s metadata beside the map on the [David Rumsey Map Collection's website](https://bit.ly/3464cFd).


![](images/mapwarper_metadata.png)
*Fig. 2: Map Warper metadata*


5. Towards the bottom of the screen, click on the Choose File button under “Upload an image file.” Navigate to the NC_SC.jpg map that you downloaded to your computer and click Create.


![](images/mapwarper_create.png)

*Fig. 3: Map Warper upload an image and create*


## Step 2: Explore the Map Warper Interface

1. You now have your map loaded into Map Warper. The interface is organized into the following tabs:

  * Show: displays only your map image
  * Edit: allows you to edit the descriptive text (metadata)
  * Rectify: used for the georeferencing itself
  * Align: a useful tool if you are stitching together multiple maps
  * Preview: shows your map on top of a modern basemap
  * Export: gives you a variety of export options and formats


![](images/mapwarper_showmap.png)
*Fig. 4: Map Warper interface*


## Step 3: Georeference your map

2. Click on the Rectify tab


3. Take a moment to move the map on the right to the North Carolina and South Carolina region. The arrows at the top of the screen move the map slightly to the North, South, East, and West and are useful when you need to make small adjustments to the map. You can zoom in and out with the slider or with your trackpad/mouse.


![](images/mapwarperzoom.png)

*Fig. 5: Map Warper zoom in and out*


* To move around a map, click the hand icon.
* To add a control point, you will click the green control point marker and click the place on the map where you want it to go. Note: The control point will not be permanently selected until you click the "Add Control Point" button below the maps.


![](images/mapwarper_tools.png)

*Fig. 6: Use the tools on the Rectify screen to pan, zoom, and add control points to your map*


4. Once you feel comfortable moving around in the maps, select your first control point. Start from the historic map and choose a location--for example, a city--that will be relatively easy to find.


5. Then, click the green control point marker on the modern map and find the same location to match them up.

![](images/mapwarper_controlpointsadded.png)
*Fig. 7: Match up your control points*

6. Click the Add Control Point button. Note: If you do not click the Add Control Point button, the next time you click on a map, the control point you added will move. This functionality gives you the flexibility to adjust your points while adding them, but can be confusing if you don’t realize that your point has moved because you didn’t click Add Control Point.

![](images/mapwarper_addcontrolpoint.png)

*Fig. 8: Click the Add Control Point button*

7. You need at least 4 or 5 points. Spread them out across your historic map--focusing on state borders, rivers, and major cities is a good strategy. If you need to delete a control point, click on “Control Points” in the Control Panel below the map.

![](images/mapwarper_controlpoints.png)

*Fig. 9: Select Control Points in the Control panel*

8. Selecting Control Points will display all of the points you have added, and enable you to delete any points that you want to re-do. You also have the option of changing the latitude and longitude manually.

![](images/mapwarper_controlpoints_delete.png)
*Fig. 10: Deleting control points and the RMS error*

*Note: You will see there is an  Error value for each control point. Map Warper uses the Root Mean Square error calculation (RMS) to evaluate the transformation of the different control points. The RMS error provides a rough guide to how consistent your control points are to one another with reference to the map's transformation and it assesses how distorted your map will be. High RMS error values indicate that your control points are less consistent with one another in comparison to a low RMS error value. It is generally recommended that you keep your error values low and replace or remove control points with high values. While the RMS error provides a good way to assess the transformation's accuracy, you should always reevaluate how well your scanned map matches up to the GIS modern map. For more information about the RMS error, please see Esri's section on interpreting the root mean square error in their [Overview of georeferencing](https://pro.arcgis.com/en/pro-app/help/data/imagery/overview-of-georeferencing.htm#ESRI_SECTION1_61F70AE3AC6C47559B3C03C74F093505)*


9. When you have enough points and think they are distributed well across your historic map, click Warp Image! at the bottom of the page. Georeferencing maps takes practice. You may find that your rectified map creates an unreadable warped map. We encourage you to try steps 7-9 again, taking into account best practices for georeferencing mentioned above, such as identifying major cities, roads, streams, and rivers that you can identify with confidence.


![](images/mapwarper_warpbutton.png)
*Fig. 11: Click Warp Image! to rectify your map*


10. You will now see the map layered on top of the OpenStreetMap.


![](images/mapwarper_openstreetmap.png)
*Fig. 12: "Georeferenced map in OpenStreetMap*


11. You can choose to view a satellite image basemap or the regular OpenStreetMap layer we’ve been using.


![](images/mapwarper_satellite.png)
*Fig 13: Georeferenced map in satellite view*


12. Click the Preview tab for a larger view of the georeferenced map. Changing the transparency using the slider can give you a sense of how accurate your georeferencing is.


![](images/mapwarper_preview.png)
*Fig 14: Map Warper Preview*


## Step 4: Export your map

13. We are now ready to export our map.  Click the Export tab


![](images/mapwarper_export.png)

*Fig 15: Map Warper Export*


14. Under Map Services, copy and paste the Tiles URL and save it to be used later in ArcGIS Online. See the example URL below:

https://mapwarper.net/maps/tile/40217/{z}/{x}/{y}.png


# Displaying your georeferenced map in ArcGIS Online

*We will now move on to loading our georeferenced map into ArcGIS Online.*

## Step 1: Create an ArcGIS Online account

1. Login to [ArcGIS Online](https://www.arcgis.com/index.html) and create a public account.


2. Once you are logged in, click on Map. This will open a new, blank map.

![](images/arcgis_mapbutton.png)
*Fig 16: ArcGIS Online Map view*


3. Click the Add drop-down menu and choose "Add layer from Web."

![](images/arcgis_addlayerfromweb.png)

*Fig. 17: ArcGIS Online Add Layer*


4. In the dropdown menu under the question, "What type of data you are referencing?," select A Tile Layer.

![](images/arcgis_tilelayer.png)
*Fig 18: ArcGIS Online Tile Layer*


5. You will be notified by ArcGIS Online that the tile layer URL must contain the level, column, and row placeholders. You will need to enter the URL you copied from Map Warper's Export Tab and change the end of the url from /{z}/{x}/{y}.png to /{level}/{col}/{row}.png. The new URL should look like:

https://mapwarper.net/maps/tile/40217/{level}/{col}/{row}.png


6. In the URL field, enter the Tile URL you copied from the export tab in Map Warper.  In the Title and Credits, you will enter your own title for this layer. For example, Title: “North Carolina and South Carolina Map 1860” and Credits: “Georeferenced Historic North Carolina 1860 map by [your name here]”. Now click "Add Layer."

![](images/arcgis_urltitlecredits.png)
*Fig 19: ArcGIS Online Tile Layer URL, Title, Credits*


7. Save your map. Add your title and at least one tag (example: ‘North Carolina’,
'South Carolina'). Save.

![](images/arcgis_savemap.png)
*Fig 20: ArcGIS Online Save Map*


8. You can now zoom to the North Carolina and South Carolina region and see your Georeferenced Map layered on top of a basemap in ArcGIS Online.

![](images/arcgis_georeferencedmap.png)
*Fig 21: ArcGIS Online georeferenced map view*


9. If you want to make your map more transparent, click on the tile layer you just added to ArcGIS Online under Contents and select the blue ellipses dots. In the drop-down menu, select Transparency and adjust the transparency of your georeferenced map using the opacity slider.

![](images/arcgis_transparency.png)
*Fig 22: ArcGIS Online Setting the Transparency*


10. Once you are done adjusting the transparency of your georeferencd map, click on the Share button in the top menu above the map.

![](images/arcgis_transparentmap.png)
*Fig 23: ArcGIS Online transparent georeferenced map*


![](images/arcgis_sharepublic.png)
*Fig 24: ArcGIS Online Share*


11. Maps created in public accounts can remain private, or be shared with "Everyone (public)". Once you choose to share with Everyone, you will be able to click "Embed in Website" to get HTML code for embedding your map on other other web platforms.

![](images/arcgis_embedwebsite.png)
*Fig 25: ArcGIS Online Embed in Website*


![](images/arcgis_embed.png)
*Fig 26: ArcGIS Online Embed HTML code*


12. You can also select ‘Create a Web App’ to load your georeferenced map into one of ArcGIS Online’s applications, such as Esri's Story Maps.

![](arcgis_createawebapp.png)
*Fig. 27: ArcGIS Online Create a Web App*


13. Esri Story Maps offers a variety of templates for you to add images, text, and other media items in order to create and publish geographic stories online.

![](arcgis_buildastorymap.png)
*Fig. 28: ArcGIS Online Web Application: Build a Story Map*
