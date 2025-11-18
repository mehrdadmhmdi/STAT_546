# Data Access

The data is available at:  
<[https://github.com/mehrdadmhmdi/546_project.git](https://github.com/mehrdadmhmdi/STAT_546.git)>

You can either download the ZIP (no Git) or clone with Git:

```bash
# install git first if needed
git clone https://github.com/mehrdadmhmdi/STAT_546.git
cd STAT_546
```

# Data Dictionary

| Variable Name                  | Type    | Description                                                                 |
|--------------------------------|---------|-----------------------------------------------------------------------------|
| `prop_id`                      | Integer | ID of the hotel                                                             |
| `time_idx`                     | Integer | Time index of the search                                                    |
| `srch_destination_id`          | Integer | ID of the search destination area                                           |
| `srch_length_of_stay`          | Integer | Number of nights searched                                                   |
| `srch_room_count`              | Integer | Number of hotel rooms specified                                             |
| `srch_saturday_night_bool`     | Integer | 1 if stay includes Saturday night; 0 otherwise                              |
| `prop_location_score1`         | Float   | First score for location desirability                                       |
| `prop_location_score2`         | Float   | Second score for location desirability                                      |
| `prop_log_historical_price`    | Float   | Log of mean historical price; 0 if unsold in last period                    |
| `prop_starrating`              | Integer | Hotel star rating                                                      |
| `prop_review_score`            | Float   | Mean customer review score (1–5)                                            |
| `random_bool`                  | Integer | 1 if search results sorted randomly; 0 if normal order                      |
| `comp_rate`                    | Integer | 1 if Expedia cheaper; 0 if same; −1 if more expensive                       |
| `comp_inv`                     | Integer | 1 if competitor unavailable; 0 if both available                            |
| `position`                     | Integer | Hotel position on Expedia search results page                               |
| `price_usd`                    | Float   | Displayed price of the hotel (per night or stay)                            |
| `promotion_flag`               | Integer | 1 if hotel had a sale price promotion; 0 otherwise                          |
| `gross_booking_usd`            | Float   | Total transaction value (may differ from `price_usd`)                       |
| `click_bool`                   | Integer | 1 if search resulted in a click; 0 otherwise                                |
| `booking_bool`                 | Integer | 1 if search resulted in a booking; 0 otherwise                              |


