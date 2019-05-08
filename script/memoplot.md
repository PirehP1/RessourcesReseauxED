[Accueil](https://github.com/PirehP1/RessourcesReseauxED/blob/master/README.md)

# Juste pour ne pas se perdre, un petit mémo : 
```R
plot(network, 
    
    vertex.color = rgb(0.8,0.4,0.3,0.8),          # La couleur des noeuds 
    vertex.frame.color = "white",                 # La couleur de la bordure des noeuds
    vertex.shape="circle",                        # La forme “none”, “circle”, “square”, etc..
    vertex.size=14,                               # taille des noeuds 
    vertex.label=LETTERS[1:10],                   # le label (intitulé) des noeuds
    vertex.label.color="white",
    vertex.label.family="Times",                  # parce qu'on peut changer de ffont  ( ex : “Times”, “Helvetica”)
    vertex.label.font=2,                          # et puis on peut souhaiter : 1 plain, 2 bold, 3, italic, 4 bold italic, 5 symbol
    vertex.label.cex=1,                           # taille des caractères 
    vertex.label.dist=0,                          # la distance entre le label et le noeud
    

    edge.color="white",                           # couleur de l'arête
    edge.width=4,                                 # taille de l'arête 
    edge.arrow.size=1,                            # taille de la pointe de l'arête 
    edge.arrow.width=1,                           # l'épaisseur de l'arête 
    edge.lty="solid",                             # le type de ligne 0 : “blank”, 1 : “solid”, 2 : “dashed”, 3  : “dotted”
    edge.curved=0.3    ,                          # on peut souhaiter une arête courbe
    )
    ```
