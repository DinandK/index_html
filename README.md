# Folium map for Streamlit Alliander

The problem with visualizing a .html file(to keep plotly plots static) in a popup on a folium map is that Streamlit reads it as a different page. However, the URL of streamlit never changes to .html, only to .py if the creator created it in such a way.
What this readme is about is working around the problem, creating a folium map, and implementing it in streamlit. We highly recommend you read [Streamlit alliander](https://github.com/DinandK/alliander) before continuing

## Preperation
First thing first, we need coordinates from the MRID's. We got it from [PDOK](https://www.nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/metadata/841b0f6f-3141-40dd-bec5-77e0065bd688).

## Data Preparation 
After getting the data from PDOK, the location.xlsx should look something like this:

| longitude  | latitude | Gebied  |
| ------------- | ------------- | ------------- |
| 51,9673788258995  | 5,84254484441544  | Arhnem  |
| 51,9651329164503  | 5,82244851029431  | Arhnem  |  

## Getting the .html files
We've created a specific .html generator to plot the different types of measurements. The .html generator can be found [here](https://github.com/DinandK/index_html/blob/main/HtmlGenerator.ipynb).

## Combining the .html files with the location data.
After you've completed all of the visuals, it's time to put everything together. The map creator (which is in the next step) loops through the location data so it is obligated to merge the plots to the specific location. The output of the location.xslx should look something like this:
| longitude  | latitude | Gebied  | html_file |
| ------------- | ------------- | ------------- | ------------- | 
| 51,9673788258995  | 5,84254484441544  | Arhnem  | 133aaad0-7a96-5385-a436-42443c49a582.html | 
| 51,9651329164503  | 5,82244851029431  | Arhnem  | 18001461-0c52-5caf-a1bf-dfe5284fa5cc.html |  

## Creating the map
After you've got your file with the desired locations and visualizations, our [creating_map notebook](https://github.com/DinandK/index_html/blob/main/creating_map.ipynb) is the next step. You can simply run this notebook with your data and get an index.html as output.

## Putting the map on a static web app
Regarding the static web app, we recommend reading the quick start. It guides you through creating a basic static web app with the index.html you've just created. It is important to note that you will need to upload the index.html and all of the plots connected to each location as .html. After this is done, the static app will automatically update the map with the corresponding plots. This URL can then be pushed to st_page.py from our [Streamlit alliander](https://github.com/DinandK/alliander) with the following code:
```python
components.iframe("https://your_static_app_url_here.net/",height= 800)
```

## Useful sources.
[Tutorial: How to Embed Interactive Plotly Visualizations in Folium Map Pop-ups ](https://towardsdatascience.com/how-to-embed-interactive-plotly-visualizations-in-folium-map-pop-ups-c69c818a8cd9)

[Quickstart: Building your first static site with Azure Static Web Apps](https://learn.microsoft.com/en-us/azure/static-web-apps/getting-started?tabs=vanilla-javascript)
