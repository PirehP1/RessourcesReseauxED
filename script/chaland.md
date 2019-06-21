

[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)


Exemple du réseau de la famille Challant, 1595-1640 en Savoie et Piémont. (voir le script LoiProba.r et données ReseauChallant.txt). Le jeu de données indique pour les relations de chaque individu dans le réseau. On peut donc évaluer les probabilités d’un individu à se connecter à d’autre dans l’environnement de cette famille nobiliaire.
    1. Représenter la distribution des relations.
    2. Estimer le nombre moyen de liens des individus.
    3. A partir de la formule de l’espérance (moyenne théorique de la loi), calculer la probabilité qu’un individu soit en lien avec un autre.


##### Importer les données 
```R
challant<-read.table("ReseauChallant.txt", header=TRUE, sep="\t")
distribution<-table(challant$liens)
plot(distribution)
summary(challant$liens)
t.test(challant$liens)
MoyenneLiens<-mean(challant$liens)
probaLien<-MoyenneLiens/max(challant$liens)
probaLiens
ks.test(distribution/sum(distribution), dbinom(0:8,8, probaLien))	# on teste pour savoir si la distribution suit une loi binomiale.
```
