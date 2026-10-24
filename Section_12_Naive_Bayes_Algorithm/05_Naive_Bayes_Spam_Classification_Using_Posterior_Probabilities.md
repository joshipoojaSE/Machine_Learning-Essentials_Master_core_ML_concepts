# Naive Bayes — Classifying Spam Emails Using Posterior Probabilities

The main goal of this lecture is to understand how **Naive Bayes** classifies a new email as **spam** or **non-spam** using probability.

---

## 1. Understand the problem

Suppose we have **1,000 emails** with labels.

| Email                  | Label $y$      |
| ---------------------- | -------------- |
| "Meeting at 10 AM"     | 0 — Non-spam   |
| "You won a free prize" | 1 — Spam       |
| "Claim your free gift" | 1 — Spam       |

We want to classify a new email, $X$, as either spam or non-spam.

This is a **supervised binary classification** problem because the training emails already have labels.

---

## 2. What does Naive Bayes calculate?

It calculates two probabilities:

$$
P(y=0 \mid X)
$$

The probability that the email is **non-spam**, given its content.

$$
P(y=1 \mid X)
$$

The probability that the email is **spam**, given its content.

These are called **posterior probabilities** because they represent the probabilities of the classes **after** observing the email.

---

## 3. How does Bayes' Theorem help?

Bayes' Theorem gives us:

$$
P(y=1 \mid X) = \frac{P(X \mid y=1)\,P(y=1)}{P(X)}
$$

Similarly:

$$
P(y=0 \mid X) = \frac{P(X \mid y=0)\,P(y=0)}{P(X)}
$$

### Understand the terms

- $P(y=1)$: **Prior** probability that an email is spam.
- $P(X \mid y=1)$: **Likelihood** — probability of observing this email content if the email is spam.
- $P(X)$: **Evidence** — overall probability of observing this email content.
- $P(y=1 \mid X)$: **Posterior** — probability that the email is spam after observing its content.

The same meanings apply to class 0, which represents non-spam.

---

## 4. How does the model make a prediction?

Suppose the model calculates these probabilities for a new email:

| Class               | Probability |                          |
| ------------------- | ----------- | ------------------------ |
| Spam (class 1)      | 75%         | `███████████████░░░░░`   |
| Non-spam (class 0)  | 25%         | `█████░░░░░░░░░░░░░░░`   |

**Prediction: Spam (class 1)**

The spam probability is higher, so the model predicts class 1.

Mathematically:

$$
\hat{y} = \arg\max_{c \in \{0,1\}} P(y=c \mid X)
$$

Here, $\arg\max$ means **choose the class with the highest probability**.

---

## 5. What is the next step in the lecture?

The lecture has explained what probabilities Naive Bayes needs and how it chooses a class. The next step is to learn how to calculate the quantities:

$$
P(X \mid y=0), \quad P(X \mid y=1), \quad P(y=0), \quad P(y=1)
$$

> **One important detail:** for text classification, Naive Bayes typically treats an email as a collection of **word features** and uses the **conditional-independence assumption** to estimate the likelihood of those features for each class. This is the key step needed to make the algorithm practical.
