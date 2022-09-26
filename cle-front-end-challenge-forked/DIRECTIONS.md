# Skills Test

Congratulations and thank you for making it this far in the interview process!
As it should have been described to you, the following is a multi-part skills test designed to reflect real-world Guardians' projects. We appreciate and value your time and we hope this test will not waste it.

## How you will be evaluated

We are evaluating the following competencies: design expertise, ability to implement functional experiences, and general approach to software engineering through coding best practices.
There are two parts to this test, **but not all parts of the test need to be completed in order to advance in the interview process.** We mostly want to see your strengths and weaknesses.

## DIRECTIONS

1. If you haven't already, create a CodeSandbox account.
2. Click on the menu icon in the top left and go to File and click Fork Sandbox --- Or just click the Fork button in the top right.
3. Continue with the directions below.
   When you are done, there is a form link in the initial email you recieved. Fill out the questions, which should include urls to your forked sandbox. Give a brief explanation of how it went and what challenges (if any) you faced. Also let us know roughly how long it took for you to complete the challenge. Speed is not what we are evaluating; we are evaluating the process as a whole and the effort it takes to complete it.
   Good luck!

### PART I

We are building a pitcher assessment page. Another developer started this project but can't finish it, so we need you to take it over. There is a service that returns a pitcher's bio and high level statistics. There are already some general placeholder components created that you should use. In addition to some basic player info, we want to show each pitch's data individually.
**When you are finished, we should have a nicely designed and formatted beginning of a pitcher assessment page along with a list of pitches and THE FOLLOWING FIELDS:**

- Pitch #
- Pitch Type
- Velo
- In Zone?
- SW/M (was it swung at and missed?)
- Batter Name (abbreviated)
- Result
  **Endpoint documentation is at the end of this document**

### PART II

Our pitching director told us that our coaches need a way to see the location of pitches in a more intuitive and natural context - on a pitch plot. The coaches want the ability to interact with a pitch in the rendered list and visualize it on a plot.
**What we need you to do is enable a user to select a pitch in the list and visualize that pitch on the PitchPlot component that we have provided you (and commented out in Player.vue).**

## Provided Endpoint Documentation For PARTS I-II

# `/players`

https://cle-fe-challenge-services.vercel.app/api/players

#### Query Params

`playerId` - OPTIONAL

#### Description

If **no query param** is passed, returns a list of playerBios

```js
// return object
{
  players: [];
}
```

If a **playerId is passed**, returns a single playerDetails object

```js
// return object
{
  playerDetails: {
  }
}
```

# `/pitches`

https://cle-fe-challenge-services.vercel.app/api/pitches?playerId=105859

#### Query Params

`playerId` - REQUIRED

#### Description

Returns a list of pitches for the passed in playerId

```js
// return object
{
  pitches: [];
}
```
