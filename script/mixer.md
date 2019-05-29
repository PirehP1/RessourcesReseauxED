
Actuellement, il n'y a pas eu d'update du paquet mixer sur R-cran. 
Nous allons donc l'installer et pour cela il faut télécharger le source pour vos machines : 
* [Ici](https://cran.r-project.org/src/contrib/Archive/mixer/mixer_1.9.tar.gz) Linux et MacOs 

Vous pouvez l'installer de cette façon : 
```R
install.packages('/votre répertoire/mixer_1.9.tar.gz' , repos = NULL, type="source")
```

Cela étant fait, nous allons utiliser le réseau des [jurys de thèses](https://github.com/PirehP1/RessourcesReseauxED/blob/master/script/theseshistoire.md). Il faut avoir préparer le réseau et utiliser **net.these**

```R
mat<-as.matrix(get.adjacency(net.these))
mat[mat>1]<-1
out <- mixer(mat,qmin=2,qmax=6)
plot(out)
```
