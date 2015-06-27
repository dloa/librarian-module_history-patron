### Librarian Module: History Patron
A librarian module that lets users reward other librarian workers for archiving history records by analyzing all submissions and identifying the "most mean" entry

1. User selects an `Alexandria History Record`
2. Get list of all fields that contain integers
3. Display a dropdown list of fields with integers, a user input field labeled `Reward goes to` with two available options, `Winner takes reward` and `Divide reward amongst entries within [int]% of mean`, a user input field labeled `Rate offered` (formatted as "amount of USD per 24 hour period") and a user input field labeled `Reward period` (formatted as a time period between reward payments)
4. On `submit`, publish a message to the Florincoin blockchain (with a transaction sent to self) in the following JSON format:
<code>{"alexandria-history-patron":{"history record":"[name of Alexandria History Record]","field":"[user-selected-field]","reward-to":"[winner,top[int]]","reward-amount":"[Rate offered]","reward-period":"[Reward period]"}}</code>
5. According to the `Reward period` set in the `Alexandria History Patron` message, monitor Florincoin blockchain periodically for new `datapoints` - if some have been submitted during the previous period (in the past hour if `Reward period` is hourly, in the past day if `Reward period` is daily, etc), do the following:
6. Get list of all `Historians` who have submitted `datapoints`
7. Get each contributor's `datapoints`
8. Get the `field` that the History Patron selected in their announcement
9. Analyze the data in this field from all `Historians` who have submitted
10. Determine how many `datablocks` there should be in each `Reward period` - ie, if the datapoints are being submitted every 5 minutes, but the reward period is set to hourly, there should be 12 `datablocks` per `Reward period` per `Historian`.
11. For each `datablock`, determine the mean value for the selected field from all `datapoints` from all `Historians`
12. Based on the `History Patron` message, select either a single winner or identify all winners within [int] percent of the mean entry.
13. Send out payments
