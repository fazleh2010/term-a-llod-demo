# testTal
docker command

```
docker pull fazleh/term-a-llod:latest 
docker run -p 8080:8080 -v ~/server/:/tmp/server/ -v ~/virtuoso_data/:/virtuoso_data/ -it term-a-llod:latest

```
Curl command for publishing your terminologies.

```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/iatesmall/' \
    "http://localhost:8080/initialize"
    
    After running command check status at http://localhost:8080/status?view=status

```
Curl command for linking  your terminology with other terminology.

```
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
