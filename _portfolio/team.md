---
title: "Team Mate Building"
excerpt: "Based on similar background with a little probability of diversity"
header:
  teaser: /assets/images/team.jpg
tags: 
  - Datathon
  - Recommendataion
  - Unsupervised Learning
  - Data Clean
  - K-Modes
  
---

## Quick View
__Goal__: Develope a way to recommend team mates for future event, data based on applicants' questionarie answer. (e.g. School, location, major...etc)

__Metrics__: Nope, this was an unsupervised learning project.

__Results__:

- Kmodes is a clustering method focus on categorical data.
- Some columns contain too many values, so appropriate clean techniques were applied to simplified data into categorical type.
- The estimation is conducted by comparing cost value between variant number of clusters, the optimal point should see decreasing rate of cost started to slow.
- The results shows that 5 clusters is optimal.
- To maintain certain diversity, I give a small probability to let small group (e.g. ppl in Art or business major) be able to join with major group(e.g. ppl in CS major).
- Of course cosine similarity is a solution to this.

## Links
[Github](https://github.com/scleeza/ML-Projects/tree/main/Team_mate_recommend)
