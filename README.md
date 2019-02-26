# 3D Portrayal Service

In Testbed 14, a first prototype of 3D Portrayal and WFS 3.0 using OpenAPI has been tested. It raises the question if we should start 3DPS 2.0 following the WFS 3.0 and OWS commons API. Let's start with a review of the 3DPS activities:

3D Portrayal Service 1.0 (OGC document 15-001r4)
https://www.opengeospatial.org/standards/3dp (approved May 2016)
Specifies queries that enable both web-based image based (conformance class view) and scene graph based (conformance class scene) rendering of 3D environments. It does NOT specify a data delivery format. 

## data delivery format of 3D Portrayal Service getScene request:

### 3D Tiles community standard (Feb 2019)
http://www.opengeospatial.org/pressroom/pressreleases/2946
http://www.opengeospatial.org/standards/3DTiles

### I3S community standard (March 2017)
https://www.opengeospatial.org/pressroom/pressreleases/2567
https://www.opengeospatial.org/standards/i3s

### Testbed 13
Implementation and testing can be found in the OGC Testbed-13: 3D Tiles and I3S Interoperability and Performance Enegineering report (OGC document 17-046)
http://docs.opengeospatial.org/per/17-046.html (March 2018)

example request:

http://tb13.igd.fraunhofer.de:8082/3dps?SERVICE=3DPS&VERSION=1.0&REQUEST=GetScene&LAYERS=manhattan&FORMAT=text/html&CRS=EPSG:4326&BOUNDINGBOX=-74.00635826977239,40.71778771238832,-73.97393297660074,40.75070138933127

The result is an XML file containing a link to the 3D tiles. This is not exactly as it should be, but it was implemented this way.

/3dps/datahoster/b042d7af-d443-450a-9e84-5c3a75209ae9/manhattan/

tileset json can be fetched here. Be aware that another port is used.

http://tb13.igd.fraunhofer.de:8083/3dps/datahoster/7ef3372e-bb7b-45a1-80a8-59b483945fbb/manhattan/tileset.json

Implementation in Cesium as a reference:
http://tb13.igd.fraunhofer.de:8080/Apps/Sandcastle/index.html?src=3DPS.html&label=Showcases
And be aware the tileset.json structure  is as it should look like in 2017. It has slightly be changed since than.

Testbed 13 also includes an example to render I3S in Cesium client as a proof of interoperability.

Testbed 13 S3D Performanve Videos on youtube:
Experiment 1: CityGML New York and Berlin, content delievry 3D Tiles
https://www.youtube.com/watch?v=OH8vczxkrow&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=15

Experiment 2: 3D Portrayal Service (CityGML New York, building heating demand, content delivery 3D Tiles) 
https://www.youtube.com/watch?v=AbyCQKH-PC4&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=17&t=4s

Experiment 3: CityGML NewYork and Berlin, content delivery I3S including rendering I3S in Cesium client
https://www.youtube.com/watch?v=ADKj6Z67YrQ&t=0s&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=8

Experiment 4: CityGML ADE and 3D Tiles
https://www.youtube.com/watch?v=qrsetxlKKjs&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=7&t=0s

Experiment 5: 3D Tiles in Geosis viewer
https://www.youtube.com/watch?v=f7Cck1iXWIo&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=10&t=0s

Experiment 6: CDB and 3D Tiles
https://www.youtube.com/watch?v=_KQRnchwRYk&t=0s&list=PLQsQNjNIDU87So4QmiSCKFmE0fv567s3m&index=3

### X3D 
(see presentation of Martin Christen, TC meeting charlotte)
3DPS GetScene implemented using Python and Flask (2015), D. Rettenmund and M. Christen, University of Applied Siences and Arts Northwesetrn Switzerland


### other resoruces:

3D Tiles support in iTown globe
http://www.itowns-project.org/

## 3DPS and WFS 3.0
### Testbed 14

https://github.com/opengeospatial/D040-Complex_Feature_Handling_Engineering_Report

API: http://steinbeis-3dps.eu:8080/tb14/API/index.html

WFS 3.0  – part: …/collections/collections-id/…
Collections-id can follow the CityGML modules such as building, vegetation, etc
3DPS part: …/collections/collections-id/scene/…
Followed by 3DPS specific parameters
Implementation: 
Façade of the existing 3DPS Server of Fraunhofer IGD (Testbed 13)

Request URL: 
http://steinbeis-3dps.eu:8080/tb14/wfs3/3D_CityModel_manhattan/collections/buildings/scene?format=application/json&bbox=-73.99562241015136,40.72227595290325,-73.9799164993194,40.749273379993284


Response Tileset: 
http://tb13.igd.fraunhofer.de:8083/3dps/datahoster/fc38b549-4989-4703-bb27-f5b4fd33fd90/manhattan/tileset.json

Demo video:
https://www.youtube.com/watch?v=3nHOvJMaKIs&list=PLQsQNjNIDU86srQjXLMB9dcSRiwQPNtfv&index=4&t=0s


## get View

3DPS getView supporting panorama images:
http://vp2-2017.3dmaps.ch/

see presentation of Martin Christen, OGC TC meeting Dec 2018
