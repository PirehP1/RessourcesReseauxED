
[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

##### Importer les données 
```R
library(igraphdata)
data(karate)
```


##### Représenter 
```R
plot(karate)
```
mémo pour les paramètres graphiques [là](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/memoplot.md)

##### Faire une matrice d'adjacence 
```R
V(karate)$comm <- membership(optimal.community(karate))
```
