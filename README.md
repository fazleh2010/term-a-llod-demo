# Publish and link your terminology
This page provides instructions on how to run the term-a-llod tool to publish and link your terminology. The user guide can be seen from the following video

[<img src="https://github.com/fazleh2010/term-a-llod-demo/blob/master/term-a-llod.png" width="50%">](https://www.dropbox.com/s/1pko14sc3qctzfr/final.mov?dl=0)

### Install term-a-llod on your machine
Install docker (https://docs.docker.com/engine/install/)
1. Download the image of term-a-llod  
```
docker pull elahi/term-a-llod:latest
```
2. Run the image as a container
```
docker run -p 8080:8080 -it elahi/term-a-llod:latest
```
Go to http://localhost:8080/status?view=status and the interface will be shown on your browser.

### Publish your terminology
3. Run the following command. Here, solar.tbx is the terminology file & mappings.default is the mapping file
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
```
- Browser: Click the **Browser** button.  You can see the terms in sorted alphabet order.  The detail of a term can be seen by clicking it. \
- Sparql:  Click the **Sparql** button. You can access your terminology through the SPARQL query.

### Link your terminology with other terminology
4.  Run the following command. 
- Here, the other terminology is intaglio terminology (https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql)
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
For example, *hole* is a term that exists both in your terminology and other terminology. To view the link do the followings: \
- Browser: Click **Browser** and select alphabet pair **G_H** and then click the term **hole**. \
- Auto-completion search: Click **Terms** and type 'ho'.\
- Sparql: Click **Sparql** and write the query for the term *hole* and then Click **Query**

## Developers
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
## Supervisor
* **Dr. Philipp Cimiano**



---
