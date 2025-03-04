# Busbud Coding Challenge

The API is deployed on Heroku at: https://challenge-recomendations-laura.herokuapp.com/suggestions

Examples of use as follows:
With query parameter: q
https://challenge-recomendations-laura.herokuapp.com/suggestions?q=Londo

Or with query parameters: latitude and longitude
https://challenge-recomendations-laura.herokuapp.com/suggestions?q=Londo&latitude=43.70011&longitude=-79.4163

## Configuration

Configuration can be done in constants located in folder '/modules/global.js'

- Constant 'WEIGHT_NAME= 0.15' means you give the algorithm a 15% of weight of importance to the matching of names. The weight of the distance is the remaining to 100%, in this case is 85%
- Constant 'MAX_POPULATION= 5000' is the requirement to show recomendations with population over 5000 inhabitants. Change it to your needs
- Constant 'NUM_DECIMALS', you can set it to show more presition in the scale
- Constant 'MIN_LENGHT_SEARCH', to make search when the query parameter 'q' is at least of this lenght
- Constant 'GOOGLE_MAPS_KEY' is set in here just to demonstrations purposes, has to be hidden
- Constant 'TSV_PATH' is the name of the file source of data for the locations search

## Requirements

Design an API endpoint that provides autocomplete suggestions for large cities.
The suggestions should be restricted to cities in the USA and Canada with a population above 5000 people.

- the endpoint is exposed at `/suggestions`
- the partial (or complete) search term is passed as a query string parameter `q`
- the caller's location can optionally be supplied via query string parameters `latitude` and `longitude` to help improve relative scores
- the endpoint returns a JSON response with an array of scored suggested matches
  - the suggestions are sorted by descending score
  - each suggestion has a score between 0 and 1 (inclusive) indicating confidence in the suggestion (1 is most confident)
  - each suggestion has a name which can be used to disambiguate between similarly named locations
  - each suggestion has a latitude and longitude
- all functional tests should pass (additional tests may be implemented as necessary).
- the final application should be [deployed to Heroku](https://devcenter.heroku.com/articles/getting-started-with-nodejs).
- feel free to add more features if you like!

#### Sample responses

These responses are meant to provide guidance. The exact values can vary based on the data source and scoring algorithm.

**Near match**

    GET /suggestions?q=Londo&latitude=43.70011&longitude=-79.4163

```json
{
  "suggestions": [
    {
      "name": "London, ON, Canada",
      "latitude": "42.98339",
      "longitude": "-81.23304",
      "score": 0.9
    },
    {
      "name": "London, OH, USA",
      "latitude": "39.88645",
      "longitude": "-83.44825",
      "score": 0.5
    },
    {
      "name": "London, KY, USA",
      "latitude": "37.12898",
      "longitude": "-84.08326",
      "score": 0.5
    },
    {
      "name": "Londontowne, MD, USA",
      "latitude": "38.93345",
      "longitude": "-76.54941",
      "score": 0.3
    }
  ]
}
```

**No match**

    GET /suggestions?q=SomeRandomCityInTheMiddleOfNowhere

```json
{
  "suggestions": []
}
```

### Non-functional

- All code should be written in Javascript.
- Mitigations to handle high levels of traffic should be implemented.
- Challenge is submitted as pull request against this repo ([fork it](https://help.github.com/articles/fork-a-repo/) and [create a pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/)).
- Documentation and maintainability is a plus.

## Dataset

You can find the necessary dataset along with its description and documentation in the [`data`](data/) directory.

## Evaluation

We will use the following criteria to evaluate your solution:

- Capacity to follow instructions
- Developer Experience (how easy it is to run your solution locally, how clear your documentation is, etc)
- Solution correctness
- Performance
- Tests (quality and coverage)
- Code style and cleanliness
- Attention to detail
- Ability to make sensible assumptions

It is ok to ask us questions!

We know that the time for this project is limited and it is hard to create a "perfect" solution, so we will consider that along with your experience when evaluating the submission.

If you choose to add other services to your challenge, we ask that you use the existing Docker Compose setup, which can be found in the `docker-compose.yml` file.

## Getting Started

### Prerequisites

You are going to need:

- `Git`
- `nvm` (or your preferred node version manager)
- `Node.js`
- `Docker` (optional)
- `Docker Compose` (optional)

### Setting up your environment

1. Begin by forking this repo and cloning your fork. GitHub has apps for [Mac](http://mac.github.com/) and
   [Windows](http://windows.github.com/) that make this easier.

2. Install [nvm](https://github.com/nvm-sh/nvm#install--update-script) or your preferred node version manager.

3. Install [Node.js](http://www.nodejs.org).

4. Install [Docker](https://docs.docker.com/install/).

5. Install [Docker Compose](https://docs.docker.com/compose/install/).

### Setting up the project

In the project directory run:

```
nvm use
npm install
```

### Running the tests

The test suite can be run with:

```
npm run test
```

### Starting the application

To start a local server run:

```
npm run start
```

#### or using Docker Compose:

```
npm run start:docker
```

either should produce an output similar to:

```
Server running at http://127.0.0.1:2345/suggestions
```
