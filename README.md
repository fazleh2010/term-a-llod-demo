# Publish and link your terminology
This page provides instructions of how to run term-a-llod tool to publish and link your terminology. There is a video to show you how to use term-a-llod tool. [term-a-llod user guice](https://github.com/fazleh2010/term-a-llod-demo/blob/master/testvedio.mov) 
### Install term-a-llod on your machine
if docker is not already installed in your machine, install docker (https://docs.docker.com/engine/install/) and test that docker is running in your machine properly.
1. downlaod term-a-llod image from Docker Hub using following command
```
docker pull fazleh/term-a-llod:latest
```
2. run the docker container in your machine
```
docker run -p 8080:8080 -it fazleh/term-a-llod:latest
```
3. Go to home page at http://localhost:8080/status?view=status and the interface will be shown on your browser.

### Publish your terminology
4. Publish your terminology using the following curl command. Here ,solar.tbx' is the terminology file and ,mappings.default' is the mapping file. Use your NameSpace.
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
```
5. Browse your terminology. In the browser,you can browse the terms in sorted alphabet order. The detail of each term can be seen from by clicking the term. You can also browse your term using sparql.
 ```
Browser:
Got o http://localhost:8080/describe
Sparql
Go to http://localhost:8080/status?view=sparql and press query button
```
### Link your terminology
6. Linking your terminology with other terminology. For example, we want to link it ,intaglio' terminology. Here https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql is sparql endpoint of the  terminology. 
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
7. Browse term links. For example 'hole' is a term that exists both in your terminology and ,intaglio' terminology
 
 ```
Browser
Got o http://localhost:8080/describe and find the term 'hole' from (i.e G_H alphabetic)in the termlist and click the term.
Search the term
Go to http://localhost:8080/status?view=search  and type 'hole' 
Sparql
Go to http://localhost:8080/status?view=sparql and write the sparql and press the button.
```

## Authors
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
* **Dr. Philipp Cimiano**



---
