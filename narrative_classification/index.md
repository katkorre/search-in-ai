## k-Shot Narrative Classification 

This experiment evaluates the Meta-LLaMA 3.1 8B-Instruct model on narrative classification using few-shot prompting.
We apply **TF-IDF with cosine similarity** to select the most semantically similar examples (shots) from the training set for each test document.
In the nexts steps , we are going to filter the prompts so as to not lose any important information because of truncation issues
The following figure shows the classification accuracy across different numbers of shots:

![Accuracy vs Number of Shots](accuracy_vs_shots.png)

