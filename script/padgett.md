[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les donnée 
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
```

#### L'approche par la richesse des familles 
##### Regarder les attributs
* E (edges)
* V (vertex)
```R
E(padgett$Business)
vertex_attr(padgett$Business)
V(padgett$Business)$name
padgett$Business[]
```

##### Faire des graphs 
```R 
plot(padgett$Business, 
     edge.arrow.size=.5, 
     vertex.label.color="black", 
     vertex.size=2.5, 
     vertex.label.dist=1.5)
```

#####  Montrer la richesse (Wealth)
```R 
V(padgett$Business)$width <- V(padgett$Business)$Wealth/sum(V(padgett$Business)$Wealth) * 100
plot(padgett$Business, 
     edge.arrow.size=.5, 
     vertex.label.color="black", 
     vertex.size=V(padgett$Business)$width, 
     vertex.label.dist=1.5)
```



```R 
tab<-data.frame(Richesse=V(padgett$Business)$width,row.names=V(padgett$Business)$name)
barplot(t(as.matrix(tab)), beside=TRUE, las=2)
```


##### Quelques indicateurs 
###### La centralité 
```R 
```
###### L'intermédiarité 
```R 
betweenness(padgett$Business)
edge.betweenness(padgett$Business)
```

```R 
closeness(padgett$Business)

evcent(padgett$Business)
``` 

