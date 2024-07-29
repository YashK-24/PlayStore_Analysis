# PlayStore_Analysis
<br>
In this project I've answered all the questions mentioned below by performing in-depth data analysis and statistical analysis using Python language.
<br>

# Objective

Google Play Store team is about to launch a new feature where in certain apps that are 
promising are boosted in visibility. The boost will manifest in multiple ways – higher priority in 
recommendations sections (“Similar apps”, “You might also like”, “New and updated games”). 
These will also get a boost in visibility in search results. This feature will help bring more 
attention to newer apps that have potential.
<br>
The task is to understand what makes an app perform well - size? price? category? multiple 
factors together? Analyze the data and present your insights in a format consumable by 
business – the final output of the analysis would be presented to business as insights with 
supporting data/visualizations.

# Tasks

1. Data clean up – Missing value treatment
    * Drop records where rating is missing since rating is our target/study variable
    * Check the null values for the Android Ver column. 
        * Are all 3 records having the same problem?
        * Drop the 3rd record i.e. record for “Life Made WIFI …”
        * Replace remaining missing values with the mode
        * Current ver – replace with most common value <br>
2. Data clean up – correcting the data types
    * Which all variables need to be brought to numeric types?
    * Price variable – remove $ sign and convert to float
    * Installs – remove ‘,’ and ‘+’ sign, convert to integer
    * Convert all other identified columns to numeric<br>
3. Sanity checks – check for the following and handle accordingly
    * Avg. rating should be between 1 and 5, as only these values are allowed on the play store.
        * Are there any such records? Drop if so.
    * Reviews should not be more than installs as only those who installed can review the app.
        * Are there any such records? Drop if so.<br>
4. Identify and handle outliers –
    * Price column
        * Make suitable plot to identify outliers in price ii. Do you expect apps on the play store to cost $200? Check out these cases
        * After dropping the useless records, make the suitable plot again to identify outliers
        * Limit data to records with price < $30
    * Reviews column
        * Make suitable plot
        * Limit data to apps with < 1 Million reviews
    * Installs
        * What is the 95th percentile of the installs?
        * Drop records having a value more than the 95th percentile<br>

# Data analysis to answer business questions
5. What is the distribution of ratings like? (use Seaborn) More skewed towards higher/lower values?
    * How do you explain this?
    * What is the implication of this on your analysis?
6. What are the top Content Rating values?
    * Are there any values with very few records?
    * If yes, drop those as they won’t help in the analysis
7. Effect of size on rating
    * Make a joinplot to understand the effect of size on rating
    * Do you see any patterns?
    * How do you explain the pattern?
8. Effect of price on rating
    * Make a jointplot (with regression line)
    * What pattern do you see?
    * How do you explain the pattern?
    * Replot the data, this time with only records with price > 0 
    * Does the pattern change?
    * What is your overall inference on the effect of price on the rating
9. Look at all the numeric interactions together –
    * Make a pairplort with the colulmns - 'Reviews', 'Size', 'Rating', 'Price'
10. Rating vs. content rating
    * Make a bar plot displaying the rating for each content rating
    * Which metric would you use? Mean? Median? Some other quantile?
    * Choose the right metric and plot
11. Content rating vs. size vs. rating – 3 variables at a time
    * Create 5 buckets (20% records in each) based on Size
    * By Content Rating vs. Size buckets, get the rating (20th percentile) for each combination
    * Make a heatmap of this
        * Annotated
        * Greens color map
    * What’s your inference? Are lighter apps preferred in all categories? Heavier? Some?
