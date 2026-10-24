# Deriving Bayes' Theorem from Conditional Probability

Bayes' Theorem is not a magic formula — it comes directly from the definition of **conditional probability**. Let's derive it step by step using a simple example:

- **A:** It is raining.
- **B:** You are going shopping.

---

## Step 1: Understand conditional probability

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

This means: *What is the probability that it is raining, **given that** you are going shopping?*

$$
P(B \mid A) = \frac{P(B \cap A)}{P(A)}
$$

This means: *What is the probability that you go shopping, **given that** it is raining?*

Here, $A \cap B$ means **both events happen together**.

---

## Step 2: Rearrange the formulas

From the first formula:

$$
P(A \mid B) \times P(B) = P(A \cap B)
$$

From the second formula:

$$
P(B \mid A) \times P(A) = P(B \cap A)
$$

Both $P(A \cap B)$ and $P(B \cap A)$ represent the **same event**: it is raining *and* you go shopping. Therefore, they are equal.

So:

$$
P(A \mid B)\,P(B) = P(B \mid A)\,P(A)
$$

---

## Step 3: Derive Bayes' Theorem

Divide both sides by $P(B)$:

> **Bayes' Theorem**
>
> $$
> P(A \mid B) = \frac{P(B \mid A) \times P(A)}{P(B)}
> $$

---

## Step 4: Connect it to a real-life example

Suppose:

| Probability | Value | Meaning |
|---|---|---|
| $P(A)$ | 0.30 | There is a 30% chance of rain. |
| $P(B \mid A)$ | 0.40 | If it rains, there is a 40% chance you go shopping. |
| $P(B)$ | 0.50 | There is a 50% chance you go shopping overall. |

Now calculate the probability that it is raining, given that you are going shopping:

$$
P(A \mid B) = \frac{0.40 \times 0.30}{0.50} = \frac{0.12}{0.50} = 0.24 = 24\%
$$

**Answer:** If you know that you are going shopping, the probability that it is raining is **24%**, based on these assumed probabilities.

---

## The most important difference

- $P(B \mid A)$: Probability of **shopping given rain**.
- $P(A \mid B)$: Probability of **rain given shopping**.

These are **not** the same probability. Bayes' Theorem helps us calculate one from the other.

---

## Memory trick

> **Start with what you know → observe new evidence → update the probability you want to find.**
