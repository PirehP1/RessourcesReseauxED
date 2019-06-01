
[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Présentation du corpus

Le corpus vise à questionner le traitement de l'actualité liée au Québec dans la presse française pendant les présidences de Charles de Gaulle. Il est constitué d'articles de presse publié entre le 14 janvier 1959 et le 24 avril 1969 qui contiennent au moins une fois le mot "Québec".

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
```R
id <- V(vocabulaire)$name
V(vocabulaire)$deg <- degree(vocabulaire)
V(vocabulaire)$bet <- betweenness(vocabulaire)
V(vocabulaire)$clos <- closeness(vocabulaire)
V(vocabulaire)$eig <- eigen_centrality(vocabulaire)$vector

```
