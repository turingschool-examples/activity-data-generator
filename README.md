## Activity Tracker Data Generator

This repo is used to generate random activity data for a set of random users - think FitBit style of data.

## How to Use the Script

1. Install dependencies with `npm install`
1. Run the main script to generate all data with `node index.js` (the files generated are written to the `output` directory)

## Adjust the Data

In the `index.js` file, there are some paramters you can adjust to change the data. The number of users to be generated and number of days of data generated for each user can be adjusted with these global variables:

```js
global.numUsers = 2;
global.numDays = 5;
```

In the `src` directory, there are files for generating kinds of data (hydration, sleep, etc.). Within these files, there are random numbers within a range that are generated for data:

```js
generateValueWithinRange([minumum value], [maximum value], [decimal precision of the generated value]);
```

## Future Plans

* Add `friends` to user object (an array of ids) - the easiest would be a one-way connection since generating mutual friends would be more difficult.
* Add normal/gaussian distribution for generating random numbers based on a user average (mu) custom for each user so that the activity data isn't so erratic and different people can have different ranges.

## Data Model

**Users**

```
[
  {
    "id": [number],
    "name": [string],
    "address": [string],
    "email": [string],
    "strideLength": [number - feet],
    "dailyStepGoal": [number - steps]
  },
  ...more users
]
```

**Activity**

```
[
  {
    "userID": [number],
    "activityData": [
      {
        "date": [string DD/MM/YYY],
        "numSteps": [number - steps],
        "minutesActive": [number - minutes],
        "flightsOfStairs": [number - flights]
      },
      ...more dates
    ]
  },
  ...more user data
]
```

**Hydration**

```
[
  {
    "userID": [number],
    "hydrationData": [
      {
        "date": [string DD/MM/YYY],
        "numOunces": [number - ounces]
      },
      ...more dates
    ]
  },
  ...more user data
]
```

**Sleep**

```
[
  {
    "userID": [number],
    "sleepData": [
      {
        "date": [string DD/MM/YYY],
        "hoursSlept": [number - hours],
        "sleepQuality": [number - unitless]
      },
      ...more dates
    ]
  },
  ...more user data
]
```

