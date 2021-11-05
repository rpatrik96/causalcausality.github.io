---
title: 'Pearls of Causality #6: Latent Structures, Stability, and Inferred Causation'
date: 2021-11-15
permalink: /posts/2021/11/poc6-latents-stability-ic/
tags:
  - causality
  - DAG
  - Latents
  - Pearl
  - Stability
  - Faithfulness
---

The model zoo of Markovian conditions is ~~fascinating~~ confusing. Let there be light!

### PoC Post Series
- [PoC #5: Markov Conditions](/posts/2021/11/poc5-markov-conditions/)
- [PoC #6: Latents and Inferred Causation](/posts/2021/11/poc6-latents-stability-ic/)

# Latent Structures

A latent structure is a pair $L = <D, O >$ , where $D$ is a causal structure over $V$ and where
$O\subseteq V$ is a set of observed variables.

## Latent Structure Preference
One latent structure $L = <D, O>$ is preferred to another $L' = <D', O>$ (written $L  \preceq L'$)

if and only if $D'$ can mimic $D$ over $O$ - that is, if and only if for every $\theta_D$ there exists a $\theta'_{D'}$, such that \(P_{[O]} (<D', \theta'_{D'}>) = P_{[O]} (<D, \theta_D>)\). Two latent structures are equivalent written $L' \equiv L$ , if and only if $L \preceq L'$ and $L \succeq L'$.

Preference is in terms of expressive power of a structure, not by its syntactic description. $L_1$ may invoke many more parameters than $L_2$ and still be preferred if $L_2$ can accommodate a richer set of probability distributions over the observables.

## Minimality of Latent Structures
A latent structure $L$ is minimal with respect to a class $\mathcal{L}$ of latent structures if and only if there is no member of $\mathcal{L}$: that is strictly preferred to $L$ -that is, if and only if for every $L' \in \mathcal{L}$: we have $L \equiv L'$ whenever $L' \preceq L$ .

## Consistency of Latent Structures

A latent structure $L = <D, O>$ is consistent with a distribution $\hat{P}$ over $O$ if $D$ can accommodate some model that generates $\hat{P}$ - that is, if there exists a parameterization $\theta_D : P_{[O]}(<D, \theta_D>)=\hat{P}$.

## Projection of Latent Structures
A latent structure $L_{[O]} = (D_{[O]}, O)$ is a projection of another latent structure $L$ if and

only if:

1 . every unobservable variable of $D_{[O]}$ is a parentless common cause of exactly two

nonadjacent observable variables; and

2. for every stable distribution $P$ generated by $L$, there exists a stable distribution

$P'$ generated by $L_{[O]} $such that $I(P_{[O]}) = I(P'_{[O]})$

A Theorem:
> Any latent structure has at least one projection.


# Stable Distributions
Let $I(P)$ denote the set of all conditional independence relationships embodied in $P$. A causal model $M = <D, \theta_D>$ generates a stable distribution if and only if $P(<D, \theta_D>)$ contains no extraneous independences-that is, if and only if $I[P(<D, \theta_D>)]\subseteq I[P(<D, \theta'_D>)]$ for any set of parameters $\theta'_D$.

# Inferred Causation
Given $\hat{P}$, a variable $C$ has a causal influence on variable $E$ if and only if there exists a directed path from $C$ to $E$ in every minimal latent structure consistent with $\hat{P}$.


# Summary
