# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :TANGUTURI TEJASWINI  
**Student ID    :2310040077  
**Date Submitted:25-03-2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**
The fitness() function calculates the total value of the items selected in the chromosome.
It first computes the total weight and total value of the packed items. If the total weight exceeds the maximum allowed weight (15 kg), the function returns 0 to mark the solution as invalid. This penalty prevents the algorithm from selecting overweight knapsack combinations.

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

The tournament_select() function randomly selects a small group of individuals from the population and compares their fitness values. The individual with the highest fitness among them is chosen as the winner. Since the best individual in each group is selected, solutions with higher fitness have a greater chance of being chosen for reproduction.

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
This line copies the best chromosome from the current generation into the next generation. This technique is called elitism in genetic algorithms. It ensures that the best solution found so far is preserved and not lost due to crossover or mutation operations.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50 |
| Best value at generation 1 |60 |
| Final best value | 77|
| Total weight of best solution (kg) |14.4/15.0kg |
| Is solution valid (Yes / No) | yes|

**Copy the printed packing list here:**
```
--------------------------------------
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
--------------------------------------
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The graph shows that the best value increases quickly in the first few generations. The biggest improvement happens at the beginning where the value rises from about 60 to around 75. After around generation 18, the graph becomes flat near 77, which means the algorithm has found a good solution and stops improving.
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         |       75          |     14.9        |  yes      |  slow              |
| 0.05         |    77             |        14.4     |  yes      |  fast              |
| 0.30         |         78        |     14.1        |      yes  |       Gradual         |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
When the mutation rate is very low (0.01), only a few changes happen in the population, so the algorithm may get stuck and improve slowly. When the mutation rate is very high (0.30), many genes change randomly, which can disturb good solutions. A moderate mutation rate like 0.05 works best because it allows some exploration while keeping good solutions. Therefore, 0.05 acts as the sweet spot for better convergence.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate 0.05 gave the best result. It provides a good balance between exploration and stability. This allows the algorithm to find better solutions without becoming too random or getting stuck early.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | 77|GA quickly improves in early generations and then stabilizes at the best solution. |
| 2 — Mutation rate | mutation_rate = 0.05 |77 |A moderate mutation rate gives better convergence than very low or very high mutation. |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
Genetic algorithms gradually improve solutions using selection, crossover, and mutation.
```

---

## Submission Checklist

- [yes ] Student name and ID filled in
- [ yes] Q1, Q2, Q3 answered
- [ yes] Experiment 1: table filled, packing list pasted, plot observation written
- [ yes] Experiment 2: results table filled (3 rows), observation and answer written
- [ yes] Summary table completed and reflection written
- [ yes] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
