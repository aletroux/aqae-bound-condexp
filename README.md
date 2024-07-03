# aqae-bound-condexp

The code takes a positive integer $N_{i}$ as input and computes the upper
bound

$$ E_i(N_i')\leq\min_{J\in\left\\{ 1,\ldots,N_{i}\right\\}} 
\left( J+(N_i-J)\left(  1 - \mathbb{P}_i (\hat{A}_i^J\in C_i^J)\right)  \right) $$

for the conditional expectation $E_i(N_i')$ of the number
$N_i'$ of shots in the $i^\text{th}$ round of the outer loop in the
Accelerated Quantum Amplitude Estimation (AQAE) algorithm, that is,
Algorithm 2 in the paper *Accelerated Quantum Amplitude Estimation
without QFT* by Alet Roux and Tomasz Zastawniak (link to be inserted). This is used in the paper to
obtain an upper bound for the expectation $E(M)$ of the computational complexity $M$ of the AQAE algorithm.

The function `PCi(E_N_i,N)` computes the conditional probability

$$ \mathbb{P}_i(\hat{A}_i^J\in C_i^J)=\mathbb{P}_i(E_i^N\leq e(\hat{A}_i^N)) $$

for given values of $E_i^N$ and $N$, where $\hat{A}_i^J$, $C_i^J$,
and $e(\hat{A}_i^N)$ are defined in the paper.

The function `PCi(E_N_i,N)` repeatedly uses the formula

$$ \mathbb{P} (X \in [a,b] ) = \mathbb{P} (X \leq b) - \mathbb{P} (X < a) = \mathbb{P}(X\leq\left\lfloor b\right\rfloor ) - \mathbb{P}(X\leq\left\lceil a\right\rceil -1) =F_{X}(\left\lfloor b\right\rfloor )-F_{X}(\left\lceil a\right\rceil -1),$$

where $X$ is a random variable with the binomial distribution $B(N,p)$, $N$ is
a positive integer, $p\in(0,1)$, $a,b\in[0,N]$, $\left\lceil
a\right\rceil$ is the ceiling of $a$ (that is, the smallest integer greater
than or equal to $a$), $\left\lfloor b\right\rfloor$ is the floor of $b$
(that is, the largest integer smaller than or equal to $b$), and
$F_{X}(x)=\mathbb{P}(X\leq x)$ is the cumulative distribution function of $X$.
