# Bayes' Theorem — Explained in Simple English

Bayes' Theorem helps us **update our belief when we get new information**.

Imagine you think it might rain today. You see dark clouds. Now you believe rain is more likely. Bayes' Theorem gives us a mathematical way to update that probability using the new evidence.

---

## 1. Real-life example: Medical testing

Imagine a disease is rare, and a doctor uses a test to check whether someone has it.

Suppose:

- **1%** of people have the disease.
- If someone **has** the disease, the test is positive **90%** of the time.
- If someone **doesn't have** the disease, the test is still positive **5%** of the time.

If a person tests positive, does that mean there is a 90% chance they have the disease?

**No!** We also need to consider how rare the disease is and how often the test gives false positives.

---

## 2. Let's calculate it with 1,000 people

Imagine testing 1,000 people:

| Group | Count | How we got it |
|---|---|---|
| People with the disease | **10** | 1% of 1,000 people |
| Positive tests among those 10 (true positives) | **9** | 90% of 10 people |
| People without the disease | **990** | 1,000 − 10 |
| Positive tests among those 990 (false positives) | **≈ 50** | 5% of 990 people = 49.5 |
| **All positive tests** | **≈ 59** | 9 + 49.5 = 58.5 |

$$
P(\text{disease} \mid \text{positive}) = \frac{9}{9 + 49.5} = \frac{9}{58.5} \approx 0.154 = 15.4\%
$$

Only **9 out of approximately 59** positive tests are true positives.

So, even though the test detects the disease 90% of the time in people who have it, a person with a positive result has only about a **15.4%** probability of having the disease under these assumptions.

---

## 3. Bayes' Theorem formula

The formula is:

$$
P(A \mid B) = \frac{P(B \mid A)\,P(A)}{P(B)}
$$

Let's understand each part (A = "has the disease", B = "test is positive"):

| Symbol | Simple meaning | Value in our example |
|---|---|---|
| $P(A)$ | Probability of the disease **before** the test (prior) | 0.01 |
| $P(B \mid A)$ | Probability of a positive test **if** the person has the disease (likelihood) | 0.90 |
| $P(B \mid \neg A)$ | Probability of a positive test if the person does **not** have the disease | 0.05 |
| $P(B)$ | **Overall** probability of getting a positive test (evidence) | 0.0585 |
| $P(A \mid B)$ | Probability of the disease **after** a positive test (posterior) | ≈ 0.154 |

The vertical bar `|` means **"given that."**

So $P(A \mid B)$ means *"the probability of A, given that B has happened."*

### Plugging in the numbers

First, the overall chance of a positive test (true positives + false positives):

$$
P(B) = P(B \mid A)\,P(A) + P(B \mid \neg A)\,P(\neg A) = (0.90)(0.01) + (0.05)(0.99) = 0.009 + 0.0495 = 0.0585
$$

Then apply Bayes' Theorem:

$$
P(A \mid B) = \frac{(0.90)(0.01)}{0.0585} = \frac{0.009}{0.0585} \approx 0.154
$$

Same answer as the 1,000-people calculation — about **15.4%**.

---

## 4. Where is Bayes' Theorem used in real life?

- **Spam detection:** Given the words in an email, how likely is it to be spam?
- **Weather forecasting:** Given current weather observations, how likely is rain?
- **Fraud detection:** Given an unusual transaction, how likely is fraud?
- **Machine learning:** Naive Bayes classifiers use Bayes' Theorem to predict classes from features.

---

## 5. Remember it this way

> **Before evidence → receive new evidence → update probability.**

Bayes' Theorem doesn't simply ask, *"How likely is the evidence if my belief is true?"*
It helps answer the reverse question: *"Given this evidence, how likely is my belief to be true?"*
