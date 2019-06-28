
Actuellement, il n'y a pas eut d'update du paquet mixer sur R-cran. 
Nous allons donc l'installer, d'une façon un peu différente, et pour cela il faut télécharger le source pour vos machines : 
* [Ici](https://cran.r-project.org/src/contrib/Archive/mixer/mixer_1.9.tar.gz) Linux et MacOs.

Il s'inscrit dans la continuité de mixnet (c++)  développé par Vincent Miele (2006)

Vous pouvez l'installer de cette façon : 
```R
install.packages('/votre répertoire/mixer_1.9.tar.gz' , repos = NULL, type="source")
```

Cela étant fait, nous allons utiliser le réseau [Sampson](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/sampson.md). Il faut avoir préparer le réseau et utiliser **sampson**

```R
mat<-as.matrix(get.adjacency(sampson))
mat[mat>1]<-1
out <- mixer(mat)
```
L'appel de mixer permet d'estimer quelques paramètres, comme le nombre de groupes  'q' d'un modèle à blocs stochastiques.



```R
plot(out)
```
