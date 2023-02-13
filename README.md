# Pet project
### Function Description

**Retention rate** is the retention rate of users. It shows how many clients return to the application for a certain period after installation.

To use the function, you need to set the start date of the period and the end date of the period.

**Requirements**
1. The start date must be greater than the end date of the period and is indicated in quotation marks.
2. The function is configured for the number of days, if you need to count by months, then you need to change the date format and bring it to the beginning of the month.

**Method of operation**
1. Accepts two entry dates (the beginning and the end of the period).
2. Reads two links (registration dates and event dates), converts the date format, makes a filter
3. Prepares both tables for merging:
* ***Registration table***: For each registration record, a list of all dates from the beginning to the end of the period is created
* ***Table with events***: adds 1 to each row so that when combining it was clear on what date the action was, reinserts columns with the date of the event in day for combining (this approach was chosen so that not only the date of the event, but also a specific action could be selected for the target action, which can be defined as an action, for example, the date where the price is indicated, and put 1 next to the columns with the price, then counting retention on them)
4. Tables are combined by columns uid and date of events (we get a table where for each user there is a registration date, all possible dates from the list, the units affixed to the dates where the action was)
5. We calculate retention through a pivot table, where for values we take the average of the columns with ones and zeros (there was an action and there was no action), or we take the amount of the column with actions and count the percentage from the first day, where 100% of users)
