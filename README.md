# how-to-mapserver-local

How to setup and use mapserver with docker on a local machine

# Prequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Visual Studio Code](https://www.docker.com/products/docker-desktop/)
- [Mapfile Syntax for VS Code](https://marketplace.visualstudio.com/items?itemName=chicoff.mapfile)

# Getting started

1. Configure layers in a [mapserver].map under `mapserver/mapfiles` (or use the exmaple layers for AEDs)
2. Add your data to `data/mapdata`
3. Add item i.e. images for layers to `data/mapitems`
4. Open the cmd-line and start the mapserver with `docker-compose up` in the repos directory (start docker desktop first)

This will download the camptocamp mapserver image from docker-hub and start the mapserver on your local machine.
To check if the services are available, just open the GetCapabilities-URL in your browser.
If you request the WMS, you should see something like this:
![AED WMS](./localhost.png "AED WMS-Layer")

You are good to go, have fun!

# Available Example GEO-Services

| Layer-Name              | Service-Url                                                                                                                                                                                                    | Description                        |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| AED                     | http://localhost/?map=/etc/mapserver/mapserver.map&service=WMS&request=GetCapabilities                                                                                                                         | WMS which serves AED data from OSM |
| AED                     | http://localhost/?map=/etc/mapserver/mapserver.map&service=WFS&request=GetCapabilities                                                                                                                         | WFS which serves AED data from OSM |
| Example Request for WMS | http://localhost/?map=/etc/mapserver/mapserver.map&service=WMS&version=1.3.0&request=GetMap&width=500&height=300&styles=&layers=AED&format=image/png&crs=epsg:4326&bbox=45.826072,5.980163,47.794121,10.464549 | WMS Overview                       |
