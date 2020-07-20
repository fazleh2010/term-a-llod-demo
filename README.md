# Publish and link your terminology
## Instruction for publish your terminology and link your with other terminology
Prerequisite
docker
Note: The instruction is written in Github. you dont need to install git. Installing docker is only Prerequisite.

### install docker
```
https://docs.docker.com/engine/install/

check whether docker is running in your machine
sudo docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.
.....
.....
```
### downlaod and install docker image
```
docker pull fazleh/term-a-llod:latest
docker run -p 8080:8080 -it fazleh/term-a-llod:latest
```
Go to home page at http://localhost:8080/status?view=status 
### publishing your terminology.
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
```
### Check your terminology
 ```
b) got o http://localhost:8080/describe
   you can see the terms in language wise and alphabet order
   Note: currently term link does not work. It is under construction.
   or 
a) go to http://localhost:8080/status?view=sparql
     press query button
```
### Linking your terminology with other terminology.
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
 ```
### Check term links
  go to http://localhost:8080/status?view=search
 ```
a) type the word in search box. An example linked term is found between two terminologies solar and intaglio terminology is 'hole'
   type 'hole' in the search box. Or
```
## The system snapshot can be seen from this [link](https://github.com/fazleh2010/term-a-llod-demo/blob/master/GuidleLIne.pdf)

---



---
