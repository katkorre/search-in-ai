# Few-Shot In-Context Learning: Intern Task Framework

## Overview
Few-shot In-Context Learning (ICL) enables large pre-trained language models (LLMs) to perform new tasks using only a few examples embedded in the prompt (called “shots”), without updating the model's parameters. Each prompt includes a support set (labeled examples) and a query input (unlabeled), which the model uses to predict the correct output. ICL is valuable in domains with limited labeled data and is commonly used in tasks like sentiment analysis, classification, and translation.

## Problem Setup
- **Support set**: $S = \{(x_i, y_i)\}_{i=1}^{K_i}\ for\ class\ \( i \)$  
- **Query input**: $x_q$ with prediction $\hat{y}_q$ = $argmax_y(\ P(y \mid x_q, S; \theta)\ )$  
- **Fixed model**: $\theta$ remains unchanged at inference time

## Goal
Assist in selecting an optimal support set $S$ for a given query $x_q$, to maximize LLM prediction quality. Selections should balance:
- **Representativeness** – cover diversity within each class
- **Informativeness** – include high-value (e.g., borderline) examples
- **Class balance** – avoid biasing toward any class
- **Diversity** – prevent redundancy within selected examples
- **Edge cases** – include ambiguous or challenging samples
- **Query similarity** – prefer samples semantically close to the query

## Sample Task: Sentiment Classification
Classify a movie review as positive (1) or negative (0). For each query review:
1. Select $k^+$ positive and $k^-$ negative examples from a pool
2. Construct a prompt like:

```
Classify the sentiment of each review.
“The film was a breathtaking journey”: 1
“Tedious watch with a predictable plot”: 0
“Captivating storyline, but pacing was slow”: ?
```

3. Evaluate how different selections of shots impact model prediction

## What Interns Will Do
- Implement a strategy to select support examples given a query $x_q$
- Explore criteria such as:
  - Maximize coverage (distance from unselected examples)
  - Maximize informativeness (uncertainty or entropy)
  - Minimize intra-class redundancy (similarity among shots)
  - Include edge cases (close to decision boundary)
  - Write simple scoring functions and selection heuristics
  - Evaluate prompt effectiveness using LLM output consistency and correctness

## Expected Outcomes
- Python functions for shot selection
- Experiments showing how different selection strategies affect ICL performance
- Suggestions on how to automate query-driven support set construction
