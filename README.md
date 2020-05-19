# LaLigaPredictor

**Still in progress**

As of now, all data is in _data.csv_. Predict results of last _N_ matches, and train with all previous ones

Main program, _LaLigaPredictor.py_ processes, cleans data and use a MLP classifier to decide outcome of unknown matches. We run the classifier several times to try different initial random-states, so we end up with a probability of each outcome (1, X, 2). If the probability of an outcome is larger than a threshold confidence value, we accept that result.

The goal is to offer the user a way to systematically predict the outcome of future matches. In betting sites such as https://sports.bwin.com/en/sports/football-4, a user could, under their own responsibility, place bets following the predicted results. A betting accuracy of 50% is our initial goal, as this means that one would always earn some amount of money.

![Alt Text](./output.gif)

---

## Getting Started

_More detailed instructions on prerequisites and usage will follow soon_

### Prerequisites

We make use of the following packages:
- re
- numpy
- pandas
- statistics
- sklearn

### Usage

One would need to edit customizable parameters in header of _LaLigaPredictor.py_ and adapt the database _data.csv_, if necessary. Then go to the main _LaLigaPredictor_ directory, open a terminal and simply run:

```
./LaLigaPredictor.py
```

---

## Database

We gather data from different sources to get two initial databases:

**Laliga database**. It contains general information about previous matches. Originally from https://www.laliga.com/, although info has been compiled in Wikipedia already (e.g. https://es.wikipedia.org/wiki/Primera_Divisi%C3%B3n_de_Espa%C3%B1a_2018-19), from where we have extracted it. It includes: Season, Round, TeamHome, Result, TeamAway, Stadium, Date, Time, Referee (only for 2016-2020), Spectators (only for 2016-2020), YellowCards (only for 2016-2020), RedCards (only for 2016-2020).

**Sofifa database**. It contains information about previous matches (but not match time), and players for each match. This info is generated by a crawler that looks in https://sofifa.com (see crawler info below). It includes: Season, Round, TeamHome, Result, TeamAway, Stadium, Date, Referee, PlayersRating, PlayersPotential.

Then, we combine these two databases:

**Final database**. It contains information of all matches and players from 2010 to 2019. The descriptors used so far are:
- Season
- Round
- Date
- Time
- TeamHome
- Result
- TeamAway
- Referee
- RatingHome
- RatingAway

### Crawler

I scrapped basic match information and players from: https://www.bdfutbol.com.

I scrapped overall ratings and potentials of players from https://sofifa.com, which contains info about FIFA games.

--- 

## License and copyright

&copy; Marcos del Cueto Cordones

Licensed under the [MIT License](LICENSE.md).
