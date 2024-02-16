[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/fbkbKZ5N)
# Asymptotic Equivalences

In the lectures, we said that logarithms with different bases don't affect the
asymptotic complexity of an algorithm. Prove that $O(\log_{2} n)$ is the same as
$O(\log_{5} n)$. Use the mathematical definition of $O$ -- do a formal proof,
not just the intuition.

I have started with the formal definition of $O$ below. Add your answer to this
markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

$T(n) \in O(f(n)) \iff \exists c, n_0: T(n) \leq c \cdot f(n) \forall n \geq n_0$

# Answer

*NOTE: I referenced [this](https://www.cuemath.com/algebra/properties-of-logarithms/) website to review logarithm properties*

Before I can prove anything pertaining to logarithms, I think it will be helpful to explain how logarithms are defined. Logarithms can be thought of as the "inverse" of exponentiation; logarithms and exponents directly coincide with each other. In fact, there exists a fairly simple method of converting between logarithmic and exponetial form:

$$
\log_{b}(a) = x \iff b^{x} = a
$$

where $b$ represents the arbitrary **base**, which is what we're interested in for this proof.

Now that we have a better understanding of Logarithm's in general, we can consisder some proven **properties of logarithms** that are imperative to prove $\mathrm{O}(\log_{2}(n)) \equiv \mathrm{O}(\log_{5}(n))$. Namely, we can use a property called the **"Change of Base Rule"** to help demonstrate the equivalence on an asymptotic scale. The change of base rule essentially states than **any** logarithm can be expressed as a quotient of two different logarithms such as:

$$
\log_{b}(a) = \frac{\log(a)}{\log(b)}
$$

Finally, we can consider the specific examples that we are interested in proving:

$$
\log_{2}(n) = \frac{\log(n)}{\log(2)}
$$

$$
\log_{5}(n) = \frac{\log(n)}{\log(5)}
$$

First, I will apply $\log_{2}(n)$ to the definition of $\mathrm{O}$:

$$\begin{align*}
& \mathrm{T}(n) \in \mathrm{O}(\log_{2}(n)) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \log_{2}(n) \forall n \geq n_0
\\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(2)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{\log(n)}{\log(2)} \forall n \geq n_0
 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(2)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{1}{\log(2)} \cdot \log(n) \forall n \geq n_0 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(2)}) \iff \exists c, n_0: \mathrm{T}(n) \leq \frac{c}{\log(2)} \cdot \log(n) \forall n \geq n_0 \\
&& \blacksquare \notag
\end{align*}
$$

Next, I will apply $\log_{5}(n)$ to the definition of $\mathrm{O}$

$$
\begin{align*}
& \mathrm{T}(n) \in \mathrm{O}(\log_{5}(n)) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \log_{5}(n) \forall n \geq n_0
\\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(5)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{\log(n)}{\log(5)} \forall n \geq n_0
 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(5)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{1}{\log(5)} \cdot \log(n) \forall n \geq n_0 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(5)}) \iff \exists c, n_0: \mathrm{T}(n) \leq \frac{c}{\log(5)} \cdot \log(n) \forall n \geq n_0 \\
&& \blacksquare \notag
\end{align*}
$$

Finally, I can generalize the pattern by replacing $2$ and $5$ with an arbitrary **constant** $b$ to represent any logarithmic base:

$$
\begin{align*}
& \mathrm{T}(n) \in \mathrm{O}(\log_{b}(n)) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \log_{b}(n) \forall n \geq n_0
\\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(b)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{\log(n)}{\log(b)} \forall n \geq n_0
 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(b)}) \iff \exists c, n_0: \mathrm{T}(n) \leq c \cdot \frac{1}{\log(b)} \cdot \log(n) \forall n \geq n_0 \\
\implies & \mathrm{T}(n) \in \mathrm{O}(\frac{\log(n)}{\log(b)}) \iff \exists c, n_0: \mathrm{T}(n) \leq \frac{c}{\log(b)} \cdot \log(n) \forall n \geq n_0 \\
&& \blacksquare \notag
\end{align*}
$$

We can see that any base of a logarithmic function can be represented as a product to satisfy the $\exists c$ quantifier within the definition of $\mathrm{O}$. More specifically, $\frac{c}{\log(b)}$ will **always** be a constant term because $c$ and $b$ are both constant terms as well. Considering that, we can see that $\log(n)$ will always grow more substantially than $\frac{c}{\log(n)}$ which renders $\frac{c}{\log(n)}$ impertinent when evaluating asymptotic bounds. 

$$
\mathrm{T}(n) \leq \frac{c}{\log(2)} \cdot \log(n) \implies \mathrm{T}(n) \in \mathrm{O}(\log(n)) \\
\mathrm{T}(n) \leq \frac{c}{\log(5)} \cdot \log(n) \implies \mathrm{T}(n) \in \mathrm{O}(\log(n)) \\
\therefore \mathrm{O}(\log_{2}(n)) \equiv \mathrm{O}(\log_{5}(n))
$$