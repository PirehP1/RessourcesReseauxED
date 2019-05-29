[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les données 
* lire pages Forsé et Degenne, *Les réseaux sociaux*, p. 112-ssq
*  méthodes fondées sur les équivalences structurales


```R
library(igraph)
library(RCurl)

path<-"sampson"
file<-"sampson.gz"
dir.create(file.path(path), showWarnings = FALSE)
url <- "https://raw.githubusercontent.com/PirehP1/RessourcesReseauxED/master/data/"
fileOut <- paste(url,file, sep="")
fileIn <- paste(path,"/", file, sep="")
bin = getBinaryURL(fileOut) 
writeBin(bin,fileIn)  

load(fileIn)
```
([Mixer](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/mixer.md))
##### Représentation 
###### Simple
```R
plot(sampson, 
    edge.arrow.size=.5, 
    vertex.label=V(sampson)$vertex.names,
    vertex.label.color="black", 
    vertex.label.dist=1.5)
```


###### Mettre en couleur les trois catégories : Loyal, Outcasts, Turks
(On prends trois coouleurs : rouge, noir, bleu)

```R
V(sampson)$color <- V(sampson)$group
V(sampson)$color[V(sampson)$color=="Turks"]<-"blue"
V(sampson)$color[V(sampson)$color=="Outcasts"]<-"black"
V(sampson)$color[V(sampson)$color=="Loyal"]<-"red"


plot(sampson, 
    edge.arrow.size=.5, 
    vertes.size=1,
    vertex.label=V(sampson)$vertex.names,
    vertex.color=V(sampson)$color, 
    vertex.label.dist=1.5)
```
mémo pour les paramètres graphiques [là](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/memoplot.md)
