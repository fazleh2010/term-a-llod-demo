# Publish and link your terminology
### Instruction for publish your terminology and link your with other terminology
Prerequisite
docker
Note: An example file of terminology (solar.tbx) and mapping file can be found in this repository.

1. install docker
```
https://docs.docker.com/engine/install/
```
2. downlaod and install docker image
```
docker pull fazleh/term-a-llod:latest
docker run -p 8080:8080 -it fazleh/term-a-llod:latest
```
3. Go to home page at http://localhost:8080/status?view=status of the system.
4. Publish your terminology using the following curl command. Here ,solar.tbx' is the terminology file and ,mappings.default' is the mapping file.
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
    
```
5. Check your terminology. In the browser,you can see the terms in sorted alphabet order. The detail of each term can be seen from by clicking the term.
 ```
Browser:
Got o http://localhost:8080/describe
Sparql
Go to http://localhost:8080/status?view=sparql and press query button
```
6. Linking your terminology with other terminology.Here https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql is sparql endpoint of the other terminology. In this case, the terminology is ,intaglio'
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
7. Check term links. For example 'hole' is a term that exists both in your terminology and other terminology ,intaglio'
 
 ```
Check from browser
Got o http://localhost:8080/describe and find the term 'hole' in the termlist and click the term.
search the term
Go to http://localhost:8080/status?view=search  and type 'hole' in search box
```

## Author
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
* **Dr. Philipp Cimiano**



---
