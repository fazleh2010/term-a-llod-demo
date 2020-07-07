# testTal
Prerequisite
```
install docker
https://docs.docker.com/engine/install/

check whether docker is running in your machine
sudo docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.
....
.....

```

Run the following commands
```
docker pull fazleh/term-a-llod:latest
docker run -p 8080:8080 -it term-a-llod:latest

check the status
http://localhost:8080/status?view=status
```


Publishing your terminology.

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
PREFIX cc:    <http://creativecommons.org/ns#> 
PREFIX void:  <http://rdfs.org/ns/void#> 
PREFIX skos:  <http://www.w3.org/2004/02/skos/core#> 
PREFIX rdfs:  <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX tbx:   <http://tbx2rdf.lider-project.eu/tbx#> 
PREFIX decomp: <http://www.w3.org/ns/lemon/decomp#> 
PREFIX dct:   <http://purl.org/dc/terms/> 
PREFIX rdf:   <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
PREFIX ontolex: <http://www.w3.org/ns/lemon/ontolex#> 
PREFIX ldr:   <http://purl.oclc.org/NET/ldr/ns#> 
PREFIX odrl:  <http://www.w3.org/ns/odrl/2/> 
PREFIX dcat:  <http://www.w3.org/ns/dcat#> 
PREFIX prov:  <http://www.w3.org/ns/prov#> 

SELECT ?s ?p ?o WHERE { 
    ?s ?p ?o .
    ?o ontolex:canonicalForm ?canform .
    ?canform ontolex:writtenRep ?rep .
} LIMIT 5

3. Check the browser

4. Search a terms

```

Linking your terminology with other terminology.

```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"
          
          
 ```
check term links
 ```
PREFIX cc:    <http://creativecommons.org/ns#> 
PREFIX void:  <http://rdfs.org/ns/void#> 
PREFIX skos:  <http://www.w3.org/2004/02/skos/core#> 
PREFIX rdfs:  <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX tbx:   <http://tbx2rdf.lider-project.eu/tbx#> 
PREFIX decomp: <http://www.w3.org/ns/lemon/decomp#> 
PREFIX dct:   <http://purl.org/dc/terms/> 
PREFIX rdf:   <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
PREFIX ontolex: <http://www.w3.org/ns/lemon/ontolex#> 
PREFIX ldr:   <http://purl.oclc.org/NET/ldr/ns#> 
PREFIX odrl:  <http://www.w3.org/ns/odrl/2/> 
PREFIX dcat:  <http://www.w3.org/ns/dcat#> 
PREFIX prov:  <http://www.w3.org/ns/prov#> 

SELECT ?s ?p ?o WHERE { 
    ?s ontolex:sameAs ?o .
} LIMIT 5
```


---



---
