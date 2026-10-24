# How to Calculate Likelihood in Naive Bayes

The **likelihood** tells us how likely the words in a new email are to appear in emails belonging to a particular class, such as **spam**.

Let's follow the lecture step by step.

---

## 1. Understand the example

Suppose the new email is:

> Get unlimited free data at a discounted price!

We want to calculate:

$$
P(X \mid Y=1)
$$

This means: the likelihood of the email's features, given that the email is spam.

The email contains multiple words, so we represent them as features:

- $x_1$ = unlimited
- $x_2$ = free
- $x_3$ = discounted
- $x_4$ = price

---

## 2. Why is calculating the likelihood difficult?

The exact probability of the entire email would depend on how the words occur **together** in spam emails.

For example, the words "unlimited" and "free" may often appear together. Therefore, knowing that one word appears can affect the probability of seeing the other.

Calculating the probability of every possible combination can be difficult.

Naive Bayes simplifies this by assuming that the features are **conditionally independent given the class**.

That means we estimate each word's probability **separately** within the spam class.

---

## 3. The likelihood formula

For an email with $n$ features, Naive Bayes uses:

$$
\boxed{P(X \mid Y=1) = \prod_{i=1}^{n} P(x_i \mid Y=1)}
$$

The symbol $\prod$ means **multiply all the terms together**.

For our example:

$$
\begin{aligned}
P(X \mid Y=1) ={}& P(\text{unlimited} \mid Y=1) \\
&\times P(\text{free} \mid Y=1) \\
&\times P(\text{discounted} \mid Y=1) \\
&\times P(\text{price} \mid Y=1)
\end{aligned}
$$

We do the same calculation for non-spam emails:

$$
P(X \mid Y=0) = \prod_{i=1}^{n} P(x_i \mid Y=0)
$$

---

## 4. Numerical example

Suppose we have already calculated these word probabilities from the training data.

| Word       | Probability in spam emails |
|------------|----------------------------|
| unlimited  | 0.8                        |
| free       | 0.7                        |
| discounted | 0.6                        |
| price      | 0.5                        |

*These numbers are illustrative.*

Multiply the probabilities:

$$
P(X \mid Y=1) = 0.8 \times 0.7 \times 0.6 \times 0.5
$$

First:

$$
0.8 \times 0.7 = 0.56
$$

Then:

$$
0.56 \times 0.6 = 0.336
$$

Finally:

$$
0.336 \times 0.5 = \boxed{0.168}
$$

So the estimated likelihood of these word features under the spam class is $0.168$.

> **Important:** This is the **likelihood**, not the final probability that the email is spam. To predict the class, we also multiply by the **prior probability** and compare the scores for spam and non-spam.

---

## 5. How do we calculate each word's probability from data?

Suppose there are **60** spam emails, and the word "free" appears in **30** of them.

A simple estimate is:

$$
P(\text{free} \mid \text{spam}) = \frac{30}{60} = 0.5
$$

This estimates the probability as **50%**.

In actual text-classification implementations, the exact calculation depends on the Naive Bayes variant and how words are represented. For example, **Multinomial Naive Bayes** uses word counts and commonly applies **smoothing** to handle words that have not appeared in a class.

---

## Remember

- **Prior:** How common is each class?
- **Likelihood:** How probable are the observed features within a class?
- **Posterior:** How probable is the class after observing the features?

The key idea in this lecture is that Naive Bayes makes likelihood calculation manageable by **multiplying the individual feature probabilities** under its conditional-independence assumption.
