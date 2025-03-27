# Bank-Marketing
(EXCEL) -  data cleaning of bank marketing campaign dataset
-
<img src= https://github.com/AndyeliSays/Bank-Marketing/blob/main/assets/cleaning_process.png>

| Column Type | Column Names | Issue | Description | Cleaning & Notes | Process |
|------------|--------------|-------|-------------|-----------------|---------|
| Duplicates | - | replace "." with "" | 12 rows removed | Remove Duplicate Function | - |
| Nulls | - | - | no missing values/noise | - | - |
| Typecast | - | - | - | - | - |
| Standardize | - | removing extra "." from jobs column, replacing "." with "_" in jobs column, replacing extra "_" in education column | - | PowerQuery | find and replace |
| Standardize | - | capitalize | - | PowerQuery | - |
| Trim | - | removing extra spaces | - | PowerQuery | - |
| client | age | - | Type of job | unknowns | - |
| client | job | - | - | unknowns | - |
| client | marital | - | Marital status of the customer | unknowns | - |
| client | education | - | Level of education | unknowns | - |
| client | default | - | Whether the customer has credit in default (binary; "yes", "no") | unknowns | - |
| client | housing | - | Whether the customer has a housing loan (binary; "yes", "no") | unknowns | - |
| client | loan | - | Whether the customer has a personal loan (binary; "yes", "no") | unknowns | - |
| campaign | poutcome | - | Outcome of the previous marketing campaign (e.g., success, failure, non-existent) | unknowns | - |
| campaign | contact | - | Contact communication type | - | - |
| campaign | month | - | Last contact month of the year | replacing abbreviations with full | find and replace |
| campaign | day_of_week | - | Last contact day of the week | replacing abbreviations with full | find and replace |
| campaign | duration | - | Last contact duration in seconds. Note: this feature is highly correlated with the target. (current campaign) | creating minutes column, only 4 rows have duration =0, no need for engagement column | if statement, special paste |
| campaign | ? | - | Number of calls performed during this campaign for this client. # of attempts to reach out (current campaign) | assuming if duration = 0, campaign > 0, otherwise error; there can't be a duration if no attempts were even made | likely # of attempts based on pivot table |
| campaign | pdays | - | Number of days since the client was last contacted from a previous campaign, how long ago was this last interaction (previous campaign) | assuming 999 placeholder signifying no prior contact, some pdays=0 values (this could either mean immediate contact less than a day) | 15 rows with pdays=0, these rows have previous > 0, could remove or mode imputation =999, if replace then pdays=999 and previous 0 (another contradiction) deleting |
| campaign | previous | - | Number of contacts performed before this campaign for this client. # of attempts to reach out (previous campaign) | assuming if previous = 0 and pdays = 999 means no prior contact at all, assuming if any pdays = 0 and previous !=0 likely an error because if there is no days since last contacted, no there should be no contacts | none |
| economic | emp.var.rate | - | Employment variation rate - quarterly indicator | no outliers | - |
| economic | cons.price.idx | - | Consumer price index - monthly indicator | no outliers - within (92-95) | - |
| economic | cons.conf.idx | - | Consumer confidence index - monthly indicator | no outliers | - |
| economic | euribor3m | - | Euribor 3-month rate - daily indicator | no outliers, continuous | - |
| economic | nr.employed | - | Number of employees - quarterly indicator | no outliers | - |
| current_campaign | y | - | Target variable: has the client subscribed to a term deposit? (binary; "yes", "no") | subscription status | - |
