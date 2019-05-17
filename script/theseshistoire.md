[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)


##### Importer les données 
```R
library(igraph)
library(RCurl)

path<-"thesehistoire"
file<-"networkthesis.csv"
dir.create(file.path(path), showWarnings = FALSE)
url <- "https://raw.githubusercontent.com/PirehP1/RessourcesReseauxED/master/data/"
fileOut <- paste(url,file, sep="")
fileIn <- paste(path,"/", file, sep="")
bin = getBinaryURL(fileOut) 
writeBin(bin,fileIn)  

net.tab<-read.csv(fileIn, sep=",", header=T)
```
#### construire le réseau 

```R
edglist <- as.matrix(net.tab)
net.these <- graph_from_edgelist(edgelist)

```
