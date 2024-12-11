# Introduction
The accompanying jupyter notebook analyzes the [In-Vehicle Coupon Recommendation](https://archive.ics.uci.edu/dataset/603/in+vehicle+coupon+recommendation) dataset available on Kaggle. The data was generated from surveys from Amazon's Mechanical Turk service. The data is related to the question of whether a person will accept a coupon recommended under different driving scenarios.

One of the five coupons available in the dataset is for higher priced restaurants ($20-50 per person). These coupons have the second lowest acceptance rate at 44.6%. 

# Question
What purchase history characteristics have the biggest differences between the higher priced restaurant coupon rejectors and acceptors which might provide guidance on how to improve the acceptance rate for these upscale restaurant coupons?

# Procedure
This investigation involves looking at the customer engagement history for different establishments (e.g. bar, coffee house, restaurant and take-out) for customers issued upscale restaurant coupons. The goal is to determine if there is a pattern in the customer's purchasing behavior that distinguishes upscale restaurant coupon rejectors from acceptors. 

The procedure is to calculate the mean probabilities of each purchase history category represented by the `Bar`, `CoffeeHouse`, `CarryAway`, `RestaurantLessThan20` and `Restaurant20To50` columns for coupon rejectors and acceptors and compare the results.

# Data Cleaning
The following actions were taken on the data set so that analysis could be performed.
* **Drop the 'car' column**  
The 'car' column contains mostly NaN values and doesn't contribute meaningful information

* **Drop the 'direction_opp' column**   
The 'direction_opp' contains the same data as the 'direction_same' column but negated. Since 'direction_opp' contains redundant information it was dropped.

* **Drop rows containing NaN values**   
Rows with NaN values comprised 4.8% of the dataset. The value is small enough that it won't significantly impact the analysis. The rows that were deleted had a similar proportion of accepted coupons (NaN rows with Y=1: 55%, non-NaN rows with Y=1: 56.9%).

* **Convert the 'age' column to numeric**   
The 'age' column was originally of dtype object and converted to numeric to facilitate data analysis. The categories 'below21' and '50plus' were replaced with 19 and 55, respectively.

* **Covert category order for the 'income' column**   
The values of the 'income' column were re-ordered to be ordinal to facilitate data analysis

# Analysis
The heatmap for upscale restaurant coupon acceptors shows the mean probability distributions for purchase history categories (Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50). For example, among coupon acceptors, 24.4% reported visiting a coffee house less than once per month. Notable observations include higher probabilities for never visiting bars (41%), dining at cheaper restaurants 1-3 times per month (41.5%), and visiting upscale restaurants less than once per month (46.7%).

Similarly, the heatmap for coupon rejectors highlights comparable patterns. For instance, rejectors are also likely to report never going to bars (42.5%) and visiting upscale restaurants less than once per month (52.7%).

The difference heatmap, calculated by subtracting acceptor probabilities from rejector probabilities, reveals the following key disparities:

Rejectors are 9.3% more likely to never visit upscale restaurants.
Rejectors are 8.7% less likely to visit upscale restaurants 1-3 times per month.
Rejectors are 10.9% less likely to visit coffee houses 1-3 times per month.
This difference heatmap suggests that rejectors tend to engage less frequently with food establishments, as indicated by higher probabilities for "never" or less frequent engagements with such venues.

# Conclusion
The analysis concludes that rejectors simply have less interactions with food establishments compared to acceptors. The purchase history differences between upscale restaurant coupon acceptors and rejectors are not particularly pronounced, offering little actionable insight to improve coupon acceptance rates.

For example, if rejectors frequented coffee houses more often, a targeted campaign could increase adoption. However, the findings suggest limited influence of past engagement on coupon acceptance. Future analyses should explore other dataset features, such as customer demographics, for opportunities. While this investigation did not identify ways to improve engagement, comparing probability distributions of different customer behavior sets is a viable technique for uncovering insights.