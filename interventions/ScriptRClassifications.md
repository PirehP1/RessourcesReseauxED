# Scripts accompagnant la conférence de Pierre  Latouche

```R
library(igraph)
library(sna)
```
## Simulation de graphes aléatoires

### Modèle d'Erdös-Rényi
```R
n = 50

mu = 0.2

# réseau dirigé sans boucle
X = matrix(0, n, n)
for(i in 1:n) {
  for(j in 1:n) {
    if(i != j) {
      X[i, j] = rbinom(1, 1, mu)
    }
  }
}

gplot(X, edge.col = "gray")

# avec une fonction et en plus rapide

erdos_renyi = function(n, mu) {
  
  X = matrix(rbinom(n^2, 1, mu), n, n)
  diag(X) = 0
  return(X)
}

X = erdos_renyi(100, 0.2)
gplot(X, edge.col = "gray")
```

#### directement sous igraph
```R
g = erdos.renyi.game(100, 0.2, directed=TRUE)
plot(g)
```

### Modèle SBM
```R
n = 50
K = 2 # nombre de clusters

#alpha = rep(1/K, K)
alpha = c(0.1, 0.9)

# PI = matrix(0.1, K, K)
# diag(PI)= 0.9

PI = matrix(c(0, 1, 1, 0), 2, 2, byrow = TRUE)

Z = t(rmultinom(n, 1, alpha))

cl = apply(Z, 1, which.max)

table(cl)

X = matrix(0, n, n)

for(i in 1:n) {
  for(j in 1:n) {
    if(i != j) {
      k = cl[i] # cluster du noeud i
      l = cl[j] # cluster du noeud j
      X[i, j] = rbinom(1, 1, PI[k, l])
    }
  }
}

pos = gplot(X, edge.col = "gray", vertex.col=cl)

gplot(X, edge.col = "gray", vertex.col=cl, coord=pos)
```
