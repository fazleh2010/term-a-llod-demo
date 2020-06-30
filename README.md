# testTal
```
Hello  (<-- two spaces)
World
```

Hello  
World

---
1. Publish your terminology
curl -X POST --progress-bar \ --verbose \ -F 'upload=@solar.tbx' \ -F 'mapping=@mappings.default' \ -F 'graph=tbx2rdf_graph' \ -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/iatesmall/' \ "https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/initialize"
2. Link your terminology with other terminology
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" -H "Content-Type: application/x-www-form-urlencoded" -X POST "https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/link"

Docker command:
1.  docker pull fazleh/term-a-llod:latest (download docker image)
2 . docker run fazleh/term-a-llod:latest (install the docker image)
