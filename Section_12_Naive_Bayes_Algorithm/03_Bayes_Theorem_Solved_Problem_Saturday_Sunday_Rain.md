# Bayes' Theorem — Solved Problem: Saturday and Sunday Rain

This note solves one Bayes' Theorem problem slowly, one small step at a time. No prior knowledge is assumed — every symbol and every calculation is explained.

---

## The Question

> **Q.** Given that the probability that it rains on Saturday is **25%**. If it rains on Saturday, the probability it rains on Sunday is **50%**. If it does not rain on Saturday, the probability it rains on Sunday is **25%**. Given that it rained on Sunday, what is the probability that it rained on Saturday?

---

## Step 0: Learn the symbols we will use

Before solving, let's understand the notation.

| Symbol | How to read it | Meaning |
|---|---|---|
| $P(\ldots)$ | "probability of …" | A number between 0 and 1 telling how likely something is. 0 = never, 1 = always. |
| $\mid$ | "given that" | Whatever comes **after** the bar is something we already know has happened. |
| $\neg$ | "not" | The event does **not** happen. |
| $\times$ | "times" | Multiplication. |

**Converting percentages to decimals:** divide by 100.

- 25% = 25 ÷ 100 = **0.25**
- 50% = 50 ÷ 100 = **0.50**

We use decimals because probabilities in formulas are written as numbers between 0 and 1.

---

## Step 1: Give the events short names

Writing "it rains on Saturday" again and again is long, so we give each event a letter:

- **S** = it rains on **Saturday**
- **U** = it rains on **Sunday** (U from "sUnday", so it doesn't clash with S)

And their opposites:

- **¬S** = it does **not** rain on Saturday
- **¬U** = it does **not** rain on Sunday

---

## Step 2: Write down what the question gives us

Let's translate every sentence of the question into symbols.

**Sentence 1:** "The probability that it rains on Saturday is 25%."

$$
P(S) = 0.25
$$

**Sentence 2:** "If it rains on Saturday, the probability it rains on Sunday is 50%."

The words "if it rains on Saturday" mean *we already know Saturday was rainy*. That is a "given that" situation, so we use the bar `|`:

$$
P(U \mid S) = 0.50
$$

Read it as: *"the probability of rain on Sunday, given that it rained on Saturday, is 0.50."*

**Sentence 3:** "If it does not rain on Saturday, the probability it rains on Sunday is 25%."

Now we know Saturday was **not** rainy, so we use ¬S after the bar:

$$
P(U \mid \neg S) = 0.25
$$

Read it as: *"the probability of rain on Sunday, given that it did not rain on Saturday, is 0.25."*

---

## Step 3: Write down what the question asks

"Given that it rained on Sunday, what is the probability that it rained on Saturday?"

- What we **know**: it rained on Sunday → **U** goes **after** the bar.
- What we **want**: did it rain on Saturday? → **S** goes **before** the bar.

$$
\text{Find: } P(S \mid U) = \; ?
$$

### ⚠️ Notice the direction has flipped

- The question **gives** us $P(U \mid S)$ → Sunday given Saturday.
- The question **asks** for $P(S \mid U)$ → Saturday given Sunday.

These are **not** the same thing. When we have one direction and need the reverse, that is exactly the job of **Bayes' Theorem**.

---

## Step 4: Find one missing piece — P(¬S)

We will need the probability that it does **not** rain on Saturday.

On Saturday, only two things can happen: it rains, or it doesn't. These two probabilities must add up to 1 (100%), because one of them is certain to happen:

$$
P(S) + P(\neg S) = 1
$$

Move $P(S)$ to the other side by subtracting it:

$$
P(\neg S) = 1 - P(S)
$$

Put in the value $P(S) = 0.25$:

$$
P(\neg S) = 1 - 0.25 = 0.75
$$

So there is a **75%** chance it does **not** rain on Saturday.

### Everything we know so far

| Symbol | Meaning | Value |
|---|---|---|
| $P(S)$ | Rain on Saturday | 0.25 |
| $P(\neg S)$ | No rain on Saturday | 0.75 |
| $P(U \mid S)$ | Rain on Sunday, if Saturday was rainy | 0.50 |
| $P(U \mid \neg S)$ | Rain on Sunday, if Saturday was dry | 0.25 |
| $P(S \mid U)$ | Rain on Saturday, if Sunday was rainy | **? (what we want)** |

---

## Step 5: Write Bayes' Theorem for our problem

The general formula is:

$$
P(A \mid B) = \frac{P(B \mid A) \times P(A)}{P(B)}
$$

In our problem, **A = S** (Saturday rain) and **B = U** (Sunday rain). Replace every A with S and every B with U:

$$
P(S \mid U) = \frac{P(U \mid S) \times P(S)}{P(U)}
$$

Let's check which parts we already have:

| Part of the formula | Do we have it? |
|---|---|
| $P(U \mid S)$ | ✅ Yes, 0.50 |
| $P(S)$ | ✅ Yes, 0.25 |
| $P(U)$ | ❌ **No** — the question never tells us the overall chance of Sunday rain |

So before we can use the formula, we must calculate $P(U)$.

---

## Step 6: Calculate P(U) — the overall chance of rain on Sunday

### The idea

Sunday rain can happen in **two separate ways**:

1. **Path 1:** It rained on Saturday **and** it rains on Sunday.
2. **Path 2:** It did **not** rain on Saturday **and** it rains on Sunday.

There is no third possibility, because Saturday is either rainy or not rainy. So the total chance of Sunday rain is the sum of these two paths.

```
                    ┌── Sunday rain (0.50) ──► Path 1: 0.25 × 0.50 = 0.125
   Saturday rain ───┤
      (0.25)        └── Sunday dry  (0.50)
Start
                    ┌── Sunday rain (0.25) ──► Path 2: 0.75 × 0.25 = 0.1875
   Saturday dry ────┤
      (0.75)        └── Sunday dry  (0.75)
```

### Why do we multiply along a path?

To get the chance of **two things both happening one after another**, we multiply:

$$
P(\text{first thing}) \times P(\text{second thing, given the first happened})
$$

Think of it as "a fraction of a fraction." If Saturday rain happens 25% of the time, and in those cases Sunday rain happens 50% of the time, then "both" happens 50% **of** 25% = 0.50 × 0.25.

### Path 1: Saturday rain AND Sunday rain

$$
P(U \mid S) \times P(S) = 0.50 \times 0.25
$$

Baby step for the multiplication: 0.50 is one half, and half of 0.25 is 0.125.

$$
0.50 \times 0.25 = 0.125
$$

### Path 2: Saturday dry AND Sunday rain

$$
P(U \mid \neg S) \times P(\neg S) = 0.25 \times 0.75
$$

Baby step: 0.25 is one quarter, and a quarter of 0.75 is 0.75 ÷ 4 = 0.1875.

$$
0.25 \times 0.75 = 0.1875
$$

### Add the two paths

$$
P(U) = \underbrace{0.125}_{\text{Path 1}} + \underbrace{0.1875}_{\text{Path 2}} = 0.3125
$$

Baby step for the addition:

```
  0.1250
+ 0.1875
--------
  0.3125
```

So the overall chance of rain on Sunday is **0.3125 (31.25%)**.

The full formula we just used is called the **Law of Total Probability**:

$$
P(U) = P(U \mid S) \times P(S) + P(U \mid \neg S) \times P(\neg S)
$$

---

## Step 7: Put everything into Bayes' Theorem

$$
P(S \mid U) = \frac{P(U \mid S) \times P(S)}{P(U)}
$$

**Top (numerator):** $P(U \mid S) \times P(S) = 0.50 \times 0.25 = 0.125$ — this is exactly Path 1 from Step 6.

**Bottom (denominator):** $P(U) = 0.3125$ — from Step 6.

$$
P(S \mid U) = \frac{0.125}{0.3125}
$$

### Baby steps for the division

Dividing decimals is easier if we remove the decimal points. Multiply the top **and** the bottom by 10,000 (doing the same to both doesn't change the answer):

$$
\frac{0.125}{0.3125} = \frac{1250}{3125}
$$

Both numbers can be divided by 625:

- 1250 ÷ 625 = 2
- 3125 ÷ 625 = 5

$$
\frac{1250}{3125} = \frac{2}{5} = 0.4
$$

Convert to a percentage by multiplying by 100:

$$
0.4 \times 100 = 40\%
$$

---

## ✅ Final Answer

$$
P(S \mid U) = 0.4 = 40\%
$$

**If we know it rained on Sunday, there is a 40% chance that it also rained on Saturday.**

---

## Step 8: Does this answer make sense? (Check with real numbers)

Formulas can feel abstract, so let's check with counting. Imagine **400 weekends**.

| | Count | How we got it |
|---|---|---|
| Rainy Saturdays | 100 | 25% of 400 |
| … of those, rainy Sundays | **50** | 50% of 100 |
| Dry Saturdays | 300 | 400 − 100 |
| … of those, rainy Sundays | **75** | 25% of 300 |
| **Total rainy Sundays** | **125** | 50 + 75 |

Now look **only** at the 125 weekends with a rainy Sunday. In how many of them was Saturday also rainy? **50.**

$$
\frac{50}{125} = 0.4 = 40\% \;\; ✓
$$

Same answer as the formula.

### Why did the chance go up from 25% to 40%?

- **Before** we knew anything about Sunday, the chance of Saturday rain was **25%** (this is called the **prior**).
- Then we learned **it rained on Sunday**. Sunday rain is more common after a rainy Saturday (50%) than after a dry one (25%), so a rainy Sunday is a clue that Saturday was probably rainy too.
- So our belief **increased** to **40%** (this is called the **posterior**).

That is the whole idea of Bayes' Theorem: **start with a belief → see new evidence → update the belief.**

---

## Summary of all steps

| Step | What we did | Result |
|---|---|---|
| 1 | Named the events | S = Saturday rain, U = Sunday rain |
| 2 | Wrote the given facts | $P(S)=0.25$, $P(U \mid S)=0.50$, $P(U \mid \neg S)=0.25$ |
| 3 | Wrote what we want | $P(S \mid U)$ |
| 4 | Found the missing opposite | $P(\neg S) = 1 - 0.25 = 0.75$ |
| 5 | Wrote Bayes' Theorem | $P(S \mid U) = \dfrac{P(U \mid S) \times P(S)}{P(U)}$ |
| 6 | Found overall Sunday rain | $P(U) = 0.125 + 0.1875 = 0.3125$ |
| 7 | Divided | $0.125 \div 0.3125 = 0.4$ |
| 8 | Checked with 400 weekends | $50 \div 125 = 0.4$ ✓ |

**Answer: 40%**
