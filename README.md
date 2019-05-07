# Ressources pour l'ED Reseaux
Ressources pour l'école doctorale sur les réseaux sociaux en histoire juin 2019


## Les données sont dans le répertoire data



## Pour utiliser 
###  Padgett 

```R
library(igraph)
library(RCurl)


path<-"padgett"
file<-"padgett.gz"
dir.create(file.path(path), showWarnings = FALSE)
url <- "https://raw.githubusercontent.com/PirehP1/RessourcesReseauxED/master/data/"
fileOut <- paste(url,file, sep="")
fileIn <- paste(path,"/", file, sep="")
bin = getBinaryURL(fileOut) 
writeBin(bin,fileIn)  


load(fileIn)
padgett

E(padgett$Business)
vertex_attr(padgett$Business)
V(padgett$Business)$name
padgett$Business[]

 plot(padgett$Business, edge.arrow.size=.5, vertex.label.color="black", vertex.size=3.5, vertex.label.dist=1.5)


