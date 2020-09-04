# Publish and link your terminology
This page provides instructions on how to run the term-a-llod tool to publish and link your terminology. The user guide can be seen from the following video

[<img src="https://github.com/fazleh2010/term-a-llod-demo/blob/master/term-a-llod.png" width="50%">](https://www.dropbox.com/s/1pko14sc3qctzfr/final.mov?dl=0)

### Install term-a-llod on your machine
Install docker (if it does not already install in your machine)(https://docs.docker.com/engine/install/).
1. Download the image of term-a-llod  
```
docker pull elahi/term-a-llod:latest
```
2. Run the docker container on your machine
```
docker run -p 8080:8080 -it elahi/term-a-llod:latest
```
Go to http://localhost:8080/status?view=status and the interface will be shown on your browser.

### Publish your terminology
3. Publish your terminology using the following command. Here solar.tbx is the terminology file and mappings.default is the mapping file. Use your NameSpace in the URL.
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
```
a) Browser: Click the Browser button. The browser will open. You can Go to you can browse the terms in sorted alphabet order and see individual term details (by clicking the term).
b) Sparql: Click the Sparql button and press the Query button for accessing the terminologies using SPARQL.

### Link your terminology
4. Linking your terminology with other terminology. For example, we want to link it ,intaglio' terminology. Here https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql is sparql endpoint of the  terminology. 
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
Check term links. For example 'hole' is a term that exists both in your terminology and ,intaglio' terminology

a) Browser: In the browser go to English>G_H> click the term 'hole'. You can see the links \
b) Search the term: Go to http://localhost:8080/status?view=search  and type 'hole'  \
c) Sparql: press sparql>query.ou can see the links \
## Developers
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
* **Dr. Philipp Cimiano**



---
