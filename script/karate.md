
[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les donnée 
```R
library(igraphdata)
data(karate)
```


##### Représenter 
```R
plot(karate)
```


##### Faire une matrice d'adjacence 
```R
V(karate)$comm <- membership(optimal.community(karate))
```
