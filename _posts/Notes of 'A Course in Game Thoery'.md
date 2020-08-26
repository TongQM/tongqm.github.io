---
layout:   post
title:    "Notes of 'A Course in Game Theory' (1)"
date:     2020-08-25
author:   "miao"
mathjax:  true
---

## Acknowledgements

These series of notes are based on ***A Course in Game Theory*** by Martin J. Obsborne and Ariel Rubinstein (1994).


## Introduction

### Definations

***Game theory** is a bag of analytical tools designed to help us understand the phenomena that we observe when decision-makers interact.* 


The basic assumptions that underlie the theory are that decision-makers pursue well-deﬁned exogenous objectives (they are rational) and take into account their knowledge or expectations of other decision-makers’ behavior (they reason strategically).    


**A game** is a description of strategic interaction that includes the constraints on the actions that the players can take and the players’ interests, but does not specify the actions that the players do take.   


**A solution** is a systematic description of the outcomes that may emerge in a family of games. Game theory suggests reasonable solutions for classes of games and examines their properties.


### Explanations and Notations

According to OR, there are four groups of game theoretic models mentioned in this book: *strategic games, extensive games with perfect information, extensive games with imperfect information and coalitional games.*


#### Dimensions

* Noncooperative and Cooperative Games
   Noncooperative games: The sets of possible actions of individual players are primitives. (strategic games, extensive games with perfect information, extensive games with imperfect information)     
   Cooperative games: The sets of possible joint actions of groups of players are primitives (coalitional games).    

* Strategic Games and Extensive Games
  A strategic game is a model of a situation in which each player chooses his plan of action once and for all, and all players’ decisions are made simultaneously.     
  An extensive game speciﬁes the possible orders of events; each player can consider his plan of action not only at the beginning of the game but also whenever he has to make a decision.

* Perfect and Imperfect Information
  In games with perfect information the players are fully informed about each others’ moves while with imperfect information they may be imperfectly informed.


#### Modelling Rationality


**With Perfect Information,**

Each decision-maker is “rational” in the sense that he is aware of his alternatives, forms expectations about any unknowns, has clear preferences, and chooses his action deliberately after some process of optimization.


*  A set $A$ of actions from which the decision-maker makes a choice. 
*  A set $C$ of possible consequences of these actions.
*  A consequence function $g:A \to C$ that associates a consequence with each action. 
*  A preference relation (a complete transitive reﬂexive binary relation) $\succeq$ on the set $C$.

Sometimes the decision-maker’s preferences are speciﬁed by giving a *utility function* $U:C \to \mathbb{R}$, which deﬁnes a preference relation $\succeq$ by the condition $x \succeq y$ if and only if $U(x)≥U(y)$.


**With Imperfect Information,**


 Individuals often have to make decisions under conditions of uncertainty. The players may be,    
 * uncertain about the objective parameters of the environment;
 * imperfectly informed about events that happen in the game;
 * uncertain about actions of the other players that are not deterministic;
 * uncertain about the reasoning of the other players.


To model decision-making under uncertainty, almost all game theory uses the theories of von Neumann and Morgenstern (1944):

*for each $a\in A$ the consequence $g(a)$ is a lottery (Prb. distribution) on $C$,*


*the decision-maker maximizes the expected value of the utility (von Neumann-Mongenstern utility) on $C$ though the judgement on expected value is subjective,*


*in this case the decision-maker has a "state space" $\Omega$, a probability measure over $\Omega$, a function $g: A\times \Omega \to C$, and a utility function $u: C \to \mathbb{R}$. He is assumed to maximizes the expected value of $u(g(a,\omega))$.*


#### Other Notations

* $\mathbb{R}$, the set of real numbers;
* $\mathbb{R}_+$, the set of nonnegative real numbers;
* $\mathbb{R}^n$, the set of vectors of $n$ real numbers;
* $\mathbb{R}^n_+$, the set of vectors of $n$ nonnegative real numbers;
* for $x, y\in \mathbb{R}^n$, $x\ge(>) y\to x_i\ge(>) y_i$ for $i=1,...,n$;
* a function $f: \mathbb{R}\to \mathbb{R}$ is increasing if $f(x)>f(y)$ whenever $x>y$;
* a function $f: \mathbb{R}\to \mathbb{R}$ is nondecreasing if $f(x)\ge f(y)$ whenever $x>y$;
* a function $f: \mathbb{R}\to \mathbb{R}$ is concave if $f(\alpha x+(1-\alpha)x')\ge \alpha f(x)+(1-\alpha)f(x')$ for all $x\in \mathbb{R}$, all $x'\in \mathbb{R}$ and all $\alpha \in [0,1]$;
* for a function $f: X\to \mathbb{R}$, denote by $\bold{argmax}_{x\in X}f(x)$ the set of maximizers of $f$;
* refer to a collection of values of some variable, one for each player, as a *profile*, denoted by $(x_i)_{i\in N}$, where $N$ is the set of players;
* for any profile $x=(x_j)_{j\in N}$ and any $i\in N$, let $x_{-i}$ be the list $(x_j)_{j\in N\backslash \{i\}}$ of elements of the profile $x$ for all players except $i$;
* similarly if $X_i$ is a set for each $i\in N$ then $X_{-i}== \times_{j\in N\backslash \{i\} }X_j$;
* a preference realtion $\succeq$ on $A$ is *continuous* if $a\succeq b$ whenever there are sequences $(a^k)_k$ and $(b^k)_k$ in $A$ that converge to $a$ and $b$ respectively for which $a^k\succeq b^k$ for all $k$;
* $|X|$ denotes the number of members of $|X|$;
* a *partition* of $X$ is a collection of disjoint subsets of $X$ whose union is $X$;
* $x\in X$ is *Pareto efficient* if there is NO $y\in X$ for which $y_i>x_i$ for all $i\in N$;
* $x\in X$ is *strongly Pareto efficient* if there is NO $y\in X$ for which $y_i\ge x_i$ for all $i\in N$ and $y_i>x_i$ for some $i\in N$.