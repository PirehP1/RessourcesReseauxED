[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les données 
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
##### Regarder les donnnées 

```R
as_data_frame(suffragettes, what="vertices")
as_data_frame(suffragettes, what="edges")
```

##### Est-ce un réseau bipartite ? 
Quelques rappels :  ([Wikipedia](https://fr.wikipedia.org/wiki/Graphe_biparti))
```R
net<-suffragettes
is.bipartite(net)
table(V(net)$Type)
table(V(net)$type)
```

##### Représenter  le réseau biparti 

Ici on ajoute des couleurs et des formes pour distinguer les deux types de sommets : 
```R
col <- c("red", "lightblue")
shape <- c("circle", "square")

plot(net,
  layout=layout.mds,
  edge.arrow.size=0.4,
  vertex.label.cex=c(0.1),
  vertex.size=3, 
  vertex.color = col[as.numeric(V(net)$type)+1],
  vertex.shape = shape[as.numeric(V(net)$type)+1],
  vertex.label.dist=1,
  vertex.label.family="Helvetica"
  )
```
Un classique (/remarquez la fonction layout/) : 
```R
plot(net,
  layout=layout.bipartite,
  edge.arrow.size=0.4,
  vertex.label.cex=c(0.1),
  vertex.size=3, 
  vertex.color = col[as.numeric(V(net)$type)+1],
  vertex.shape = shape[as.numeric(V(net)$type)+1],
  vertex.label.dist=1,
  vertex.label.family="Helvetica"
)

```

mémo pour les paramètres graphiques [là](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/memoplot.md)

##### Quelques indicateurs
```R
id <- V(net)$label
types <- V(net)$type        
deg <- degree(net)
bet <- betweenness(net)
clos <- closeness(net)
eig <- eigen_centrality(net)$vector

net_centrality <- data.frame(id, types, deg, bet, clos, eig)
net_centrality
```
Il y a beaucoup de *composantes connexes* dans ce réseau, non ? 

```R
gclust <- clusters(net)
gclust$no
numLCC = gclust$csize[4]
sub.net = induced.subgraph(net, V(net)[which(gclust$membership == which.max(gclust$csize))])

```
On peut représenter juste les relations entre les femmes 

```R
proj.net<-bipartite.projection(sub.net)
adj.net<-get.adjacency(proj.net$proj1,sparse=FALSE,attr="weight")

plot(proj.net$proj1,
    edge.width=E(proj.net$proj1)$weight^2,
    edge.color="gray",
    vertex.size=5, 
    vertex.label=V(proj.net$proj1)$name,
    vertex.label.cex=0.7,
    vertex.color = "red",
    vertex.label.dist=1,
    vertex.label.family="Helvetica"
    )
```
