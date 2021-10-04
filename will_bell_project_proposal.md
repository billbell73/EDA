#EDA Project Proposal

##Question/Need

- My client is a major tenant of concession premises in NYC subway stations called 'Crazy Donuts'.
- Crazy Donuts is about to renegotiate its leases with the MTA
- To be well-prepared for these negotiations, Crazy Donuts wants to obtain a detailed understanding of how footfall (i.e. turnstile entries and exits) at its relevant stations has been affected by the Coronavirus Pandemic
- Negotiations will happen on a premises-by-premises basis: the greater the reduction in relevant footfall, the greater rent discount Crazy Donuts is likely to request with respect to a specific premises.
- Crazy Donuts is most interested in passenger traffic during what it calls 'Donut Time' which is roughly the morning commute period (the morning surge in passengers)
- Crazy Donuts will provide a list of stations (turnstiles?) where it is a tenant


#### Central Question:
 - Quantify the reduction if any in total entries and exits for certain specific stations and turnstiles between 2019 and equivalent periods in 2021, for the morning commute period. 

#### Sub Questions:
- (How to choose where Crazy Donuts has concessions)
- How to get data from MTA website into SQL database, and how to then query using Pandas
- How to clean / dedupe data
- How to choose periods of 2021 that will be most informative. E.g. before and/or after Delta variant hit? Use pandemic data to make choice of comparison period?
- How to aggregate the most relevant data from a given period: i.e. ideally weekday mornings commute-time only (or all week at tourist stations?)
- How to define morning commute period? Using MTA data itself?
- How to make sure 2019 and 2021 data is comparable - e.g. are we talking exact same times of day for data from both years at the various locations?


#### Additional questions if time:
- Crazy Donuts would like to see how changes in footfall relate to changes in Covid case numbers in the city. The negotiations may involve talking about the likely future trajectory of the pandemic, and it would be useful to know how different scenarios might affect footfall.
- Crazy Donuts wonder if new work patterns could provide expansion opportunities. As a result, they want to know about anywhere across NYC where entries / exits have increased since before the pandemic.


## Data Description

#### MTA Turnstile Data
- MTA Turnstile Data from 2019 (i.e. pre-pandemic) and 2021.
- Sample data: 

*C/A,UNIT,SCP,STATION,LINENAME,DIVISION,DATE,TIME,DESC,ENTRIES,EXITS*  
*A002,R051,02-00-00,LEXINGTON AVE,456NQR,BMT,09-27-14,00:00:00,REGULAR,0004800073,0001629137,*  
*A002,R051,02-00-00,LEXINGTON AVE,456NQR,BMT,09-27-14,04:00:00,REGULAR,0004800125,0001629149,*
- Each turnstile has unique C/A, UNIT, SCP, and STATION combination
- Comparing pre-pandemic and more recent ENTRIES and EXITS for given turnstiles and stations will be central to the project
- ENTRIES and EXITS values are the 'cumulative register value' for a device

#### NYC Pandemic Data
- NYC pandemic data from NYC Health is available on Github in csv file format
- I intend to use https://github.com/nychealth/coronavirus-data/blob/master/trends/cases-by-day.csv
- This has various data relating to case count since the start of the pandemic; e.g. daily case count

##Tools

- Pandas
- SQL / SQLAlchemy
- Matplotlib
- Seaborn

## MVP Goal

A visualisation which compares pre-pandemic and more recent morning footfall at the relevant stations 