[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les donnée 
```R
library(igraph)
library(RCurl)


path<-"suffragettes"
file<-"suffragettes.gz"
dir.create(file.path(path), showWarnings = FALSE)
url <- "https://raw.githubusercontent.com/PirehP1/RessourcesReseauxED/master/data/"
fileOut <- paste(url,file, sep="")
fileIn <- paste(path,"/", file, sep="")
bin = getBinaryURL(fileOut) 
writeBin(bin,fileIn)  


load(fileIn)
suffragettes
```

##### Représenter  le réseau biparti 

Ici on ajoute des couleurs et des formes pour distinguer les deux types de sommets ([Wikipedia](https://fr.wikipedia.org/wiki/Graphe_biparti))
```R
net<-suffragettes
col <- c("red", "lightblue")
shape <- c("circle", "square")

plot(net,
  vertex.size=3, 
  vertex.color = col[as.numeric(V(net)$type)+1],
  vertex.shape = shape[as.numeric(V(net)$type)+1],
  vertex.label.dist=1
)
```
