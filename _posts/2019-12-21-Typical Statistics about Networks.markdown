---
layout: post
title:  "Some Typical Statistics about Networks"
date:   2019-12-21
author: "miao"
mathjax:  true
---



# Some Typical Statistics about Networks  
记一些微观里图论分析常用的统计量
## Overall Statistics
### Degree Distributions
Trivial to understand, here three popular distributions are mentioned.

##### Poisson

$P(d=k)=\frac{\lambda^ke^{-\lambda}}{k!},$  

which is usually considered as the approximation of binomial distribution especially when n is large and p is a small.
##### Regular
One-point distribution,    

$$P(d=k)=1, P(d\ne k)=0.$$

##### Scale-free
This is a distribution where the probabiliy is proportional to $-\gamma$ power of degree,    

$$P(d=k)=ck^{-\gamma}.$$    

So why does it called Scale-free distribution? Just because,    

$$\frac{P(d=\mu k)}{P(d=k)}=\mu^{-\gamma},$$    

regardless of the specific k.    
PS: no situation where $k=0$.

### Diameter
Define $l_{ij}$ as the least length between i and j (also called geodesic).
The diameter of a network or a component is,  

$$max\{l_{ij},i\ne j,i,j\in N\},$$    

namely length of the longest geodesic in a network or a component.
### Average Path Length
Selfevidently, average path length implies,   

$$avg\{l_{ij},i\ne j,i,j\in N\}.$$

### Cliquishness
A clique means a maximal completely connected (i.e. each node in the set has a link to all the other nodes in the set) subnetwork of a given network. Particularly a clique should have at least three nodes, otherwise any pairing nodes will be considered as a clique, which doesn’t make sense.    

Intuitively, cliquishness can be measured by the number and size of cliques in the network. However, there are more quantitative methods to measure cliquishness.

##### Overall  Clustering
Formula goes first,    

$$Cl(g)=\frac{\sum_{i;j\ne i;k\ne j;k\ne i}g_{ij}g_{jk}g_{ik}}{\sum_{i;j\ne i;k\ne j}g_{ij}g_{jk}}.$$    

It seems complicated but just evaluates the proportion of complete triple subnetworks over the number of triple networks with two links.
##### Average Clustering
Before presenting average clustering of the network, individual clustering needs introducing,    

$$\begin{aligned}Cl_i(g)&=\frac{\sum_{j\ne i;k\ne j;k\ne i}g_{ij}g_{jk}g_{ik}}{\sum_{j\ne i;k\ne j;k\ne i}g_{ij}g_{ik}}\\
\\&=\frac{\#\{jk\in g|k\ne j,j,k\in N_i(g)\}}{d_i(g)[d_i(g)-1]/2}\end{aligned}$$     

Note that both the numerator and the denominator are the sum of relationships fixed on point i, compared with overall clustering.

Based on individual clustering, average clustering can be derived as,  

$$Cl^{avg}(g)=\frac{\sum_iCl_i(g)}{n},$$    

namely the algebraic average of individual clusterings. Actually, the difference between overall and average clustering lies on weights of individual clusterings. Average clustering just endows the same weight on every node while overall clustering allocates weights according to the number of triple relationships of each node.

##### Transitive Clustering
For directed networks, the general approach is to ignore directions and calculate as common undirected networks. Besides, transitive clustering can also be used to appraise the cliquishness of a network,    

$$Cl^{TT}(g)=\frac{\sum_{i;j\ne i;k\ne j}g_{ij}g_{jk}g_{ik}}{\sum_{i;j\ne i;k\ne j}g_{ij}g_{jk}}$$   

Note the main difference between $Cl^{TT}(g)$ and $Cl(g), Cl^{avg}(g)$ is that i becomes the origin point in directed triple structures rather than the midpoint in undirected triple structures.

## Individual Statistics
The most important and common property of nodes in networks is *Centrality*. Here seven different methods of measuring centrality are discussed.

### Degree Centrality
Trivial,    

$$Ce_i^D(g)=d_i(g)/(n-1),$$    

where $d_i(g)$ is the degree of i and $n-1$ is the most degrees a node can have.

### Closeness Centrality
Closeness centrality manages to measure centrality from the perspective of distance.

##### Average Distance
Selfevidently,    

$$Ce_i(g)=(n-1)/\sum_{j\ne i}l(i,j),$$    

Note that this centrality is the reciprocal of the average distance from node i to all the other nodes, which makes the statistic positively related with closeness.

##### Decay Centrality
The idea is that each node from i should be endowed with a certain weight according its distance from i and i gets the centrality value by adding all the other nodes’ weights.    

$$Ce_i(g)=\sum_{j\ne i}\delta^{l(i,j)}$$    

Given $\delta$, one can calculate the centrality with the length of geodesics from i to all the other nodes.
When $\delta\to1$, the centrality basically measures how large the component where i lies is.    
When $\delta\to0$, the centrality is approximately proportional to the degree centrality.     
When $\delta$ is intermediate, node i is rewarded for how close it is to other nodes.

##### Betweenness Centrality
The philosophy is to quantize how well a node is situated in terms if the paths it lies on.    
Let $P(kj)$ be total # of geodesics between k, j and $P_i(kj)$ be # if geodesics between k, j that i lies on.
Reasonably for individual pair (k, j), the centrality can be denoted as,     

$$Ce_i^B(g)=P_i(kj)/P(kj)$$     

Average it across pairs,     

$$Ce_i^B(g)=\sum_{k\ne j;i\not\in\{k, j\}}\frac{P_i(kj)/P(kj)}{(n-1)(n-2)/2},$$    

where the denominator is the number of pairs not including i.

##### Katz Prestige Centrality
Prestige means a node’s importance determined by how important its neighbors are.    
An important idea is that the attention (importance) of neighbors is definite and needs to be allocated across its neighbors. Katz just uses the uniform distribution so that i’s prestige is exactly the sum of the prestige of i’s neighbors divided by their respective degrees,    

$$P_i^K(g)=\sum_{j\ne i}g_{ij}\frac{P_i^K(g)}{d_i(g)}$$     

Based on the ajacency matrix, we denote,    

$$\hat g_{ij}=g_{ij}/d_j(g),$$    

which normalize the weight of node j to be distributed to its neighbors. Then with matrix and vector centrality can be denoted with an equation,    

$$P^K(g)=\hat gP^K(g),$$    

then we get,    

$$(\mathbb{I}-\hat g)P^K(g)=0$$     

Apparently the centrality vector is the eigenvector of $\hat g$ with eigenvalue 1. Also note that $P^K(g)$ is only determined up to a scalefactor.

##### Eigenvector Centrality
Based on Katz Prestige Centrality, eigenvector centrality can be developed. The idea is that the centrality of a node is proportional to the sum of the centrality of its neighbors. So in this case there’s no division of centrality to allocate to neighbors.     

$$\lambda C^e(g)=gC^e(g),$$    

where $\lambda$ is the proportional factor reflecting the linear relationship between a certain node’s centrality and the sum of neighbors’ centrality. In a certain way, $\lambda$ can be chosen randomly only if the vector is not negative. Conventionally the largest eigenvalue is used.    
Additionally one can think of the Katz Prestige as a form of eigenvector centrality when we have adjusted the network adjacency matrix to be weighted.

##### Katz-2 Centrality
This method jumps out of the one-step neighbors and extends the self-referential value to all the other nodes. With power of adjacency matrixes, one can find k-step neighbors from node i easily. Multiplied by a degenerate weight $a^k$, the importance of i due to the k-step neighbos can be derived.    

$$P^{K2}(g,a)=ag\mathbb{1}+a^2g^2\mathbb{1}+a^3g^3\mathbb{1}+..., 0<a<1$$   

Another understading can also be applied to this method, where we can assign some base value, say $ag\mathbb{1}$. Then a given node gets its base value, plus $a$ times the base value of each node it has a direct link to, plus $a^2$ times the base value of each node that it has a walk of length 2 to, plus ...     
With this understanding one can write the original centrality vector in,    

$$P^{K2}(g,a)=ag\mathbb{1}(1+ag+a^2g^2+...)$$    

The final solution, $P^{K2}(g,a)=\mathbb{I}-ag)^{-1}ag\mathbb{1}$.    
PS: just the formula of the sum of geometric progression.
##### Bonacich Centrality
Bonacich Centrality is derived from the second understanding of Katz Prestige-2 Centrality. It just starts with base values of $ag\mathbb{1}$ and then uses another weight $b$ to evaluate walks of length k to other nodes by a factor $b^k$ rather than $a^k$. Accordingly,     

$$Ce^B(g,a,b)=(\mathbb{I}-bg)^{-1}ag\mathbb{1}$$
 



先写这么多，后面会更进图论在微观分析中的应用。
