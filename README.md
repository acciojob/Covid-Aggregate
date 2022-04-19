# Covid Aggregate Template Repo

# Instructions

During any virus outbreak, the governments are supposed to constantly look at
the new hotspots, mortality rates, etc of different states to aid the states with
necessary equipment and help. To do so, the officials must get correct and reliable
statistics immediately.

We are supposed to create an API server that performs some aggregation tasks on
the Covid data. This data is stored in the MongoDB server.
You can create this dataset on your desktop if you have MongoDB installed on it.
Run node /src/createDatabase.js . Read the file carefully to understand how it is
working.

Don't forget to run npm i to install dependencies

# Acceptance Criteria
We are supposed to expose our server at 5 endpoints.

## GET localhost:8080/totalRecovered
should calculate the total number of recovered patients across all the
given states(also UTs).

Returned response should be in the format {data: {_id: "total", recovered:

## GET localhost:8080/totalActive
should calculate the total number of active patients across all the given
states(also UTs).

Active cases = (infected-recovered)
Returned response should be in the format {data: {_id: "total", active:
11574}}.

## GET localhost:8080/totalDeath
should calculate the total number of deaths across all the given
states(also UTs).

Returned response should be in the format {data: {_id:"total", death:
11574}}.

## GET localhost:8080/hotspotStates
Every state is declared as a hotspot of its rate value is greater than 0.1.
rate value can be calculated as ((infected - recovered)/infected)
rate value should be rounded to 5th decimal point using MonogDb built-in
feature $round.

Returned response should be in the format

```
{data: [{state: "Maharastra",
rate: 0.17854}, {state: "Punjab", rate: 0.15754}]}
```

## GET localhost:8080/healthyStates
Every state is declared as a healthy state of its mortality value is less than
0.005.

mortality value can be calculated as (death/infected).

mortality value should be rounded to 5th decimal point using MonogDb
built-in feature $round.

Returned output should be in the format {data: [{state: "Maharastra",
mortality: 0.0004}, {state: "Punjab", mortality: 0.0007}]}.

## Note
Mongoose should be used.

Tests are Case Sensitive so be careful with output data

Output format should be as mentioned above.

Round off the data using built-in feature $round

## Important instructions for passing tests:
1.  Ouput the data in JSON format exactly as it is shown in the problem statements
2. in the output for /hotspotStates and /healthyStates, the state names must be in alphabetical order.
3. Do not edit your database after creation as the tests are hardcoded.
