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


> [!NOTE] Определение $\lim_{x\to \infty}{x_n=A\in \mathbb R}$
> Если $(x_n)$ — **бесконечно большая последовательность (ББП)**, то $\left(\frac{1}{x_n}\right)$ — **бесконечно малая последовательность (БМП)**.
