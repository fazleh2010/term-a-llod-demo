# testTal
The system suppose to be running only by docker pull and docker run. But currently it is not working like that. Currently, it uses github. Completelty running from docker is on progress.

Run the following commands
```
git clone -b demo https://github.com/FrankGrimm/tbx2rdf_staging.git
docker build . -t term-a-llod:latest
docker run -p 8080:8080 -v ~/server/:/tmp/server/ -it term-a-llod:latest

```
Curl command for publishing your terminologies.

```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
    
    After running command check status at http://localhost:8080/status?view=status

```
Check that Virtuoso server is running.

```
1. Service status
http://localhost:8080/status?view=status

2. Check sparql

3. Check the browser

4. Search a terms

```

Curl command for linking  your terminology with other terminology.

```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" -H "Content-Type: application/x-www-form-urlencoded" -X POST "http://localhost:8080/link"

Check status at http://localhost:8080/status?view=status
```


---



---
