# testTal
Curl command for publishing and linking terminologies.

```
1. Publish your terminology
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@simple1.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/iatesmall/' \
    "https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/initialize"
    
Check status at https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/status?view=status
```
Curl command for publishing and linking terminologies.

```
    
2. Link your terminology with other terminology
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" -H "Content-Type: application/x-www-form-urlencoded" -X POST "https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/link"

Check status at https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdftest/status?view=status
```

Docker command to download and install image

---
```
1.  docker pull fazleh/term-a-llod:latest (download docker image)
2 . docker run fazleh/term-a-llod:latest (install the docker image)
```



---
