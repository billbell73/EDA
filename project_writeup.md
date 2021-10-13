## Crazy Donuts' NYC subway station footfall analysis

### Abstract

My client is Crazy Donuts. Crazy Donuts has concession premises which it rents from the MTA in 14 diverse subway stations across NYC. Crazy Donuts is about to re-negotiate its leases for all these premises with the MTA. In order to be well-prepared for these negotiations, the company wants to obtain a detailed understanding of how passenger footfall at its relevant stations has been affected by the Coronavirus Pandemic. I found good evidence to support Crazy Donuts requesting very substantial rent discounts. Passenger footfall has not only reduced significantly everywhere, but has shown a pattern of being notably slow to recover from its reduced levels, even during the massive fall in case numbers that NYC saw until mid-2021. At the same time, because the level and the pattern over time of the footfall reduction shows significant differences amongst the 14 stations, it may be worth negotiating on a premises-by-premises basis.

### Design

Crazy Donuts approached me. I use publicly available data and undertake exploratory data analysis with the hope of producing some insights, the communication of which might be assisted with data visualisations. The end goal is to for Crazy Donuts to enter their lease re-negotiations better prepared.

### Data
* I use public MTA turnstile data to compare passenger footfall in the first 9 months of 2021 at the 14 relevant stations with an equivalent period pre-pandemic, namely the first 9 months of 2019. 
* I also use NYC Health Covid-19 daily case data for 2021, available on Github.

### Algorithms
I look at how the comparative data varies between the stations generally, and how it varies over the 9 months.

The workhorse of much of my analysis is the `stations_monthly` python function which takes a Pandas dataframe of raw MTA data, plus arguments of month, year and turnstile direction (i.e. 'ENTRIES' or 'EXITS') and returns a Pandas series of the relevant entry or exit count for each station for that month. The function that `stations_monthly` calls to get the daily turnstile count takes a `max_counter` argument and discards any daily turnstile counts above this number. This is necessary because many large daily counts are actually measurement errors. 

In my separate `max_counter_analysis` Jupyter Notebook I investigate what is an appropriate number for this `max_counter` parameter. I choose the value 15,000 on the basis that very few legitimate daily counts are above this number. This is from a visual inspection of the largest daily counts in descending order: gauging the level at which the numbers are no longer due to counters resetting. (Incidentally, I regard this as a potentially fruitful area for future work. Ideally, either the `max_counter` number would be set at different levels for different stations, or another method would be found for eliminating these measurement errors. The current one-size-fits-all approach sees a few legitimate counts discarded, and a fair number of bogus counts included).

Generally, I create dataframes for the 9 month period by iterating over the `stations_monthly` function for each relevant month, and append the results to a list. I then create a new dataframe from that list of Pandas series, which can be used as the basis for a visualisation. 

### Tools
* Various Python libraries including Pandas for downloading MTA turnstile data to local database
* SQLite database for storing turnstile data locally 
* Python SQLAlchemy for accessing database and getting data into Pandas dataframes
* Pandas for fetching data from remote NYC Health csv files
* Pandas and NumPy for data cleaning and exploratory data analysis
* Pandas, Matplotlib and Seaborn for data visualization

### Communication
The methodology and results of this project have been communicated via this document, and via a recorded presentation and its slide-deck.