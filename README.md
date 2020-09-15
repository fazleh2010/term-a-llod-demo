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
3. Run the following command. Here 
- solar.tbx is the terminology file & 
- mappings.default is the mapping file
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
```
a) Browser: Click the Browser button.  You can see the terms in sorted alphabet order.  The detail of a term can be seen by clicking it. \
b) Sparql:  Click the Sparql button. You can access your terminology through the SPARQL query.

### Link your terminology
4.  Link your terminology with other terminology. For example, you want to link intaglio terminology with your terminology. The SPARQL endpoint of the intaglio terminology is https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql 
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
Check term for link detail. For example, 'hole' is a term that exists both in your terminology and intaglio terminology. Do the following\
a) Browser: In the browser go to English>G_H> click the term 'hole'. You can see the link of this term with other terminology \
b) Search the term: Click Terms button and type 'ho'. The auto-completion suggestion will guide you\
c) Sparql: Click Sparql and query the term 'hole' 

## Developers
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
## Supervisor
* **Dr. Philipp Cimiano**



---
