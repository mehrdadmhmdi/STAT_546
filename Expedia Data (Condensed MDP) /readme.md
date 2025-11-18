# Data Structure and Information
---
## What This Data Is and How We Restructure It?

The raw Expedia Hotel Search data records **what a user saw on a search results page** on Expedia.  
In the raw files ([available here](https://www.kaggle.com/competitions/expedia-personalized-sort/)), each time a user performs a search (`srch_id`), Expedia shows a **list of hotels**, and the raw dataset contains **one row per *property shown* in that list**.  

So at the raw level:

- **One search = one results page.**  
- **Each row = one hotel shown on that page.**  
- A single `srch_id` can therefore appear many times (because many hotels were shown).

---

## What structure we transform this into?

We convert this raw list-view dataset into a **longitudinal, time-indexed format**:

1. Each *search destination* (identified by `srch_destination_id`) is treated as its own **small MDP**.
2. Searches for the same destination are **sorted chronologically**, and we assign a **time index** (`time_idx = 1, 2, 3, ...`) representing the order in which searches happened at that destination.
3. For each search (`srch_id`), we **collapse all the property-level rows into a single row**, summarizing:
   - state features of the search,
   - action-like aggregate descriptors of the list,
   - reward outcomes such as revenue or clicks.

This produces a **long-format panel** where:

- **Each row = one search event**  
- **Each destination = one trajectory over time**  
- **`time_idx` = the search order for that destination**

This is the format required for downstream **longitudinal modeling and RL-style analysis**.

---

## Is this a MDP setting?

We can do (did) the following on the data to test the MDP setting:

1. Estimated lag-(k) autocorrelations  and tests.
2. Compared models for $\mathbb{E}[R_t |  A_t]$ vs  $E[R_t | S_t, A_t]$. So we can compare Bandit vs MDP 
3. Compared $E[S_{t+1} | S_t,A_t])$ vs  $E[S_{t+1} | S_t, A_t, S_{t-1}, A_{t-1}]$. Markov property

4. Used feature importance in E[R_t |  S_t,A_t]) to quantify the influence of each state/action dimension. 


I think we can conclude the following from the plots:

Autocorrelations show weak but real temporal structure.

 Predicting reward improves when adding states

Predicting next states depends on previous states/actions
It is not strictly Markov, but somehow Markov. I think removing some variables we can restore strictly markov too.  


I think we can safely conclude that this is offline RL (MDP) problem, not a bandit.
---

## Data Dictionary , ID, State, Action, Reward

