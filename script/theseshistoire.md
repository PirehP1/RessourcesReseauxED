[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)


#### Importer les données 
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
#### Construire le réseau 

```R
edgelist <- as.matrix(net.tab)
net.these <- graph_from_edgelist(edgelist, directed=FALSE)

```

#### Représenter 
```R
plot(net.these,
  layout=layout.mds,
  edge.arrow.size=0.4,
  vertex.label.cex=c(0.1),
  vertex.size=2, 
  vertex.label.dist=1,
  vertex.label.family="Helvetica"
  )
```
#### Détecter des groupes 
On préférera le terme **groupe** à celui de **communautés**, les groupes sont produits par des algorithmes. 

##### fonction modularité 
```R
md <- cluster_edge_betweenness(net.these)
modularity(md)
```
