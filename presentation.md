---
marp: true
theme: uncover
class: invert
title: Sleeping Mice
paginate: true
---

# Sleeping Mice

Antoine Blancy, Alexey Paulot

25.02.2023

---

# Introduction

<br>

- States of Mice:

  - Awake, REM Sleep, Non-REM Sleep
    <br>

---

# Data available

**185 mice in groups of genetic clones**:

- For each mouse, we have a recording every $1/4s$ over 4 days:

  - Brainwave activity: amplitudes of varying frequencies,

  - EEGv, EMGv, Temperature,

  - State of the mouse

---

# Goal

## Using only the data provided, **predict the state of mice**.

---

# Approach

- At first:
  - Predict the state of a single mouse using its own data.
- Then:
  - Predict the state of a group of random mice using other mice's data.
- Finally
  - Predict the state of cloned mice using the data of a single "related" mouse.

---

# Presentation

#### 1. Data preprocessing and features

#### 2. Predicting the state of a single mouse

#### 3. Predicting the state of a group of mice

---

# 1. Data preprocessing and features

---

# Data preprocessing

- We have 4 days of data:
  - Only use the first 2 days, as they are undisturbed.
- 401 frequencies:
  - Min-max normalization
- EEGv, EMGv, Temperature:
  - Min-max normalization

---

### Features:

#### Frequencies

![bg left width:90% drop-shadow](img/freq.png)

- Brainwave activity is different in each state.
- Second half of the frequency spectrum is "useless"

---

### Features:

![bg right width:90% drop-shadow](img/eeg.png)

#### EEGv, EMGv, Temperature

Looks promising looking at the graphs.

But it varries wildly between different mice.

---

# Labels

**Multi-class classification** problem.

- 3 classes: Awake, REM Sleep, Non-REM Sleep

- One hot encoding, becomes:

  - [0,0,1] -> Awake
  - [0,1,0] -> Non-REM Sleep
  - [1,0,0] -> REM Sleep

- We can also infer the genetic group of a mouse if needed

---

#

---
