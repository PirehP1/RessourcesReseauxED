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

plot(padgett$Business)
plot(padgett$Wedding)
