
[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Deux ou trois choses du corpus

##### Importer les données 
```R
library(igraphdata)
library(ggraph)
library(RCurl)


path<-"CoocsVocabulaire"
file<-"vocabulaire.gz"
dir.create(file.path(path), showWarnings = FALSE)
url <- "https://raw.githubusercontent.com/PirehP1/RessourcesReseauxED/master/data/"
fileOut <- paste(url,file, sep="")
fileIn <- paste(path,"/", file, sep="")
bin = getBinaryURL(fileOut) 
writeBin(bin,fileIn)  


load(fileIn)
vocabulaire
```
##### Accéder aux données
