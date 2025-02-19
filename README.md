# Predicting Customer Subscription to Term Deposits in a Banking Institution

## Business Understanding
The bank conducts direct marketing campaigns via phone calls to promote term deposits. However, contacting every client is costly and time-consuming. The challenge is identifying which clients are most likely to subscribe to a term deposit, allowing the bank to reduce marketing costs by focusing on potential subscribers, improve conversion rates by targeting the right customers, and enhance customer experience by avoiding unnecessary calls.

## Objective
To develop a predictive model that helps a Portuguese banking institution determine the likelihood of a client subscribing to a term deposit based on direct marketing campaign data.

## Data Understanding
- Age : Age of the client
- Job : Type of job (categorical: admin, blue-collar, entrepreneur, housemaid, management, retired, self-employed, services, student, technician, unemployed, unknown)
- Marital : Marital status (categorical: divorced, married, single, unknown; note: divorced means divorced or widowed)
- Education : Education level of the client
- Default : Has credit in default? If a client has credit in default, they may be less likely to invest in a term deposit
- Balance : Average yearly balance
- Housing : Has housing loan? Clients with existing loans might have lower investment capacity
- Loan : Has personal loan? Clients with existing loans might have lower investment capacity
- Contact : Contact communication type (categorical: cellular, telephone)
- Day : Last contact day of the week
- Month : Last contact month of year 
- Duration : Last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
- Campaign : Number of contacts performed during this campaign and for this client (numeric, includes last contact)
- Pdays : Number of days that passed by after the client was last contacted from a previous campaign (numeric; -1 means client was not previously contacted)
- Previous : Number of contacts performed before this campaign and for this client
- Poutcome : Outcome of the previous marketing campaign (categorical: failure, nonexistent, success)
- Y : Has the client subscribed a term deposit? Yes or No

## Process Flow

## Prediction Results
