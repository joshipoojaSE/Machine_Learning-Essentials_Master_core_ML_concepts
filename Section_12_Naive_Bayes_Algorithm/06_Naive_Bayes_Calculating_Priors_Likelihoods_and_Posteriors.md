# Naive Bayes — How to Calculate Probabilities

This lecture explains how **Naive Bayes** learns from labeled emails to predict whether a new email is **spam** or **non-spam**.

---

## 1. Calculate the prior probabilities

The lecture assumes there are **100 emails** in the training dataset:

- **60** spam emails, labeled **1**
- **40** non-spam emails, labeled **0**

The **prior probability** is the proportion of emails belonging to each class.

$$
P(y=1) = \frac{60}{100} = 0.6
$$

$$
P(y=0) = \frac{40}{100} = 0.4
$$

**Why?** Before looking at the content of a new email, the training data tells us that 60% of the emails are spam and 40% are non-spam.

---

## 2. Calculate the likelihoods

Suppose a new email says:

> "Get unlimited mobile data at 95% discounted price!"

We want to estimate how likely this email's words are in each class.

- $P(X \mid y=1)$: **Likelihood** of the email content given the spam class.
- $P(X \mid y=0)$: **Likelihood** of the email content given the non-spam class.

The lecture uses illustrative values:

$$
P(X \mid y=1) = 0.8
$$

$$
P(X \mid y=0) = 0.21
$$

> **Note:** These are example numbers, not values calculated from actual email counts. The next stage of the course will explain how to calculate likelihoods from word frequencies.

---

## 3. Calculate the class scores

Bayes' Theorem gives:

$$
P(y \mid X) = \frac{P(X \mid y)\,P(y)}{P(X)}
$$

For classification, we can compare the **numerators** because $P(X)$ is the same for both classes.

### Spam score

$$
P(X \mid y=1)\,P(y=1) = 0.8 \times 0.6 = \boxed{0.48}
$$

### Non-spam score

$$
P(X \mid y=0)\,P(y=0) = 0.21 \times 0.4 = \boxed{0.084}
$$

The spam score is higher, so the model predicts **spam**.

---

## 4. Why can we ignore $P(X)$?

The lecture explains that the denominator is **identical** for both class probabilities.

The total probability of observing the email can be calculated using the **law of total probability**:

$$
P(X) = P(X \mid y=0)\,P(y=0) + P(X \mid y=1)\,P(y=1)
$$

Using the illustrative values:

$$
P(X) = (0.21 \times 0.4) + (0.8 \times 0.6)
$$

$$
P(X) = 0.084 + 0.48 = 0.564
$$

We can now calculate the actual **posterior probabilities**:

$$
P(y=1 \mid X) = \frac{0.48}{0.564} \approx 85.11\%
$$

$$
P(y=0 \mid X) = \frac{0.084}{0.564} \approx 14.89\%
$$

| Class               | Score  | Posterior |
| ------------------- | ------ | --------- |
| Spam (class 1)      | 0.48   | ≈ 85.11%  |
| Non-spam (class 0)  | 0.084  | ≈ 14.89%  |

The spam probability is higher, so the prediction remains **spam**. Dividing by $P(X)$ changes the numbers but not which class wins.

---

## 5. Important correction for understanding

For a real text-classification system, $X$ contains **multiple words**. Naive Bayes uses the **conditional-independence assumption** to estimate the combined likelihood from individual word probabilities. The lecture's values 0.8 and 0.21 are simplified examples; they are not yet showing the full word-by-word calculation.

### Remember the process

1. Calculate the **prior** from class counts.
2. Calculate the **likelihood** from training data.
3. **Multiply** likelihood by prior for each class.
4. **Compare** the class scores and choose the larger one.
