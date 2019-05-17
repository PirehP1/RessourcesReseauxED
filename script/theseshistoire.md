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
On préférera le terme **groupe** à celui de **communautés**, les groupes sont produits par des algorithmes. Un billet de Laurent Beauguitte sur ce thème ([Ici](https://arshs.hypotheses.org/1314)). 

Il y a beaucoup de **composantes connexes**, on va s'interesser à la plus grande. 
```R
gclust <- clusters(net.these)
gclust$no
numLCC = gclust$csize[4]
sub.net = induced.subgraph(net.these, V(net.these)[which(gclust$membership == which.max(gclust$csize))])
```

##### l'algorithme dit "louvain"
```R
louv <- cluster_louvain(sub.net)
modularity(louv)
```

```R
plot(louv,  sub.net,
  layout=layout.mds,
  edge.arrow.size=0.4,
  vertex.label.cex=c(0.2),
  vertex.size=2, 
  vertex.label.dist=1,
  vertex.label.family="Helvetica",
  main = paste("Louvain", round(modularity(louv),2), sep = " ")
  )
```


##### fonction modularité

```R
# md <- cluster_edge_betweenness(sub.net)
# modularity(md)
```
