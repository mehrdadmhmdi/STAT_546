# Structure
## What This Data Is and How We Restructure It

The raw Expedia Hotel Search data records **what a user saw on a search results page** on Expedia.  
In the raw files ([available here](https://www.kaggle.com/competitions/expedia-personalized-sort/)), each time a user performs a search (`srch_id`), Expedia shows a **list of hotels**, and the raw dataset contains **one row per *property shown* in that list**.  

So at the raw level:

- **One search = one results page.**  
- **Each row = one hotel shown on that page.**  
- A single `srch_id` can therefore appear many times (because many hotels were shown).

---

## What structure we transform this into

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
