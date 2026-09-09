$$\text{последовательность ограниченная если } \exists M>0\;\forall n \in \mathbb N: |a_n| \le M .$$
$$
\nexists \lim_{n\to\infty}(-1)^{n-1}
$$
$$
\mathbb RU = \{-\infty\} \cup \{+\infty\} \cup \{\infty\} \cup \mathbb R
$$
$$
\text{если } \forall R>0\; \exists \; N\in \mathbb N:\forall n > N\;\;|x_n|>R
$$
$$
\text{если } \{x_n\} -\text{ББП} \Rightarrow \{\frac{1}{x_n}\}-\text{БМП} 
$$
$$
\text{если } \{\frac{1}{x_n}\} -\text{БМП} \Rightarrow \{x_n\}-\text{ББП} 
$$
# ББП → БМП

> [!NOTE] Утверждение
> Если $(x_n)$ — **бесконечно большая последовательность (ББП)**, то $\left(\frac{1}{x_n}\right)$ — **бесконечно малая последовательность (БМП)**.

## Доказательство

Пусть

$$
x_n \to \infty.
$$

По определению ББП:

$$
\forall M>0\ \exists N\in\mathbb{N}:
\quad n>N \Rightarrow x_n>M.
$$

Возьмём произвольное

$$
\varepsilon>0.
$$

Положим

$$
M=\frac{1}{\varepsilon}.
$$

Тогда существует такое $N$, что при $n>N$:

$$
x_n>\frac{1}{\varepsilon}.
$$

Так как $x_n>0$, можем обратить неравенство:

$$
0<\frac{1}{x_n}<\varepsilon.
$$

Следовательно,

$$
\left|\frac{1}{x_n}-0\right|<\varepsilon.
$$

А это и есть определение **бесконечно малой последовательности**:

$$
\frac{1}{x_n}\to0.
$$

> [!SUCCESS] Ответ
>
> $$
> \boxed{x_n\to\infty
> \quad\Rightarrow\quad
> \frac{1}{x_n}\to0}
> $$

Таким образом, **обратная последовательность к ББП является БМП**.


> [!NOTE] Определение $\lim_{n\to \infty}{x_n=A\in \mathbb R}$
> Если $\forall  U(A)  \exists N:\forall n>N: x_n\in U(A)$

Почти правильно, но есть небольшая ошибка в записи: **предел берётся у последовательности по n→∞n\to\infty**, а не x→∞x\to\infty.

Правильное определение:

lim⁡n→∞xn=A  ⟺  ∀U(A) ∃N∈N ∀n>N: xn∈U(A)\boxed{ \lim_{n\to\infty}x_n=A \iff \forall U(A)\ \exists N\in\mathbb N\ \forall n>N:\ x_n\in U(A) }

где U(A)U(A) — **любая окрестность точки AA**.

Если через ε\varepsilon, то эквивалентно:

∀ε>0 ∃N∈N ∀n>N:∣xn−A∣<ε\boxed{ \forall\varepsilon>0\ \exists N\in\mathbb N\ \forall n>N: |x_n-A|<\varepsilon }

То есть идея у тебя **абсолютно верная**: начиная с некоторого номера NN, все члены последовательности попадают в любую заранее заданную окрестность AA.