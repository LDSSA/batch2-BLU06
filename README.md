# batch2-BLU06-instructors

## What is in this BLU?

The third and final BLU in the Data Wrangling Specialization is about data transformation, using both Pandas and sklearn-like transformers.

In this BLU, we'll learn how to use Pandas to perform most data transformations tasks functionally. We'll also use some methods to combine data frames. Then, we will introduce data transformations performed differently in training and test sets. In a way, such data transformations are akin to modeling: we fit the data transformer on training data and use it later to transform data coming through a pipeline. Finally, in the exercises, we combine all these elements in setting up complete data transformation pipelines to feed modeling.

We're going exploring.

## How to use this repo
1. Install all the needed dependencies, specified in the requirements.txt file
* Install via pip
```
pip install -r requirements.txt
```

2. Go through the Learning Notebooks (they are in the Learning Notebooks/ folder)
3. Do the Exercise notebook, and submit it on [the portal](http://portal.lisbondatascience.org) as usual

## "I need help understanding something."
You can and should ask for help, be it about Learning Notebooks, Exercises, or anything else. Please check out the [How to Ask for Help](https://github.com/LDSSA/wiki/wiki/How-to-ask-for-and-give-help), and remember not to share code when asking for help about the exercises!

## "I think I've found a bug."
This repo is entirely open source and is continuously improving over time. When you spot a mistake, check the [issues](https://github.com/LDSSA/batch2-BLU06/issues). If it hasn't, please open an issue, explaining in details where it is (e.g., in what notebook, and on what line), and how to reproduce the error. If it is an easy fix, feel free to make a pull request.

## About the data

The New York Philharmonic played its first concert on December 7, 1842.

The data documents all known concerts, amounting to more than 20,000 performances.

The [Leon Levy Digital Archives](https://archives.nyphil.org/) provides an interface for searching printed programs alongside other digitized items.

We organized the performances as follows:

* The Program is the top-most level element in our dataset
* A Program is defined as performances in which the repertoire, conductors, and soloists are the same
* A Program is associated with an Orchestra (e.g., New York Philharmonic) and a Season (e.g., 1842-43)
* A Program may have multiple Concerts with different dates, times and locations
* A Program's repertoire may contain numerous Works (e.g., two different symphonies by Beethoven)
* A Work can have multiple Soloists (e.g., Mahler on the harpsichord, Strauss or Bernstein on the piano or Isadora Duncan listed as a dancer).

## Data dictionary

### Programs

Programs are under `/data/programs/`, arranged by season (i.e., each season as a separate `{season}.csv` file).

| Variable      | Type [dtype]    | Meaning                             |
| :-------------|:----------------| :-----------------------------------|
| GUID          | string [object] | Leon Levy Digital Archives ID       |
| ProgramID     | int [int64]     | Local NYP ID                        |
| Orchestra     | string [object] | Full orchestra name                 |
| Season        | string [object] | Sep 1 - Aug 31, displayed "1842-43" |

### Concerts

| Variable  | Type [dtype]    | Meaning                                                                        |
| :---------|:----------------| :------------------------------------------------------------------------------|
| GUID      | string [object] | Leon Levy Digital Archives ID                                                  |
| ProgramID | int [int64]     | Local NYP ID                                                                   |
| ConcertID | int [int64]     | Concert ID, for same program                                                   |
| EventType | float [float64] | NYP event type                                                                 |
| Location  | string [object] | Geographic location of concert                                                 |
| Venue     | string [object] | Name of hall, theater, or building where the concert took place                |
| Date      | string [object] | Full ISO date used, but ignore TIME part (1842-12-07T05:00:00Z = Dec. 7, 1842) |
| Time      | string [object] | Actual time of concert, e.g. "8:00PM"                                          |

### Works

| Variable      | Type [dtype]    | Meaning                            |
| :-------------|:----------------| :----------------------------------|
| GUID          | string [object] | Leon Levy Digital Archives ID      |
| ProgramID     | int [int64]     | Local NYP ID                       |
| WorkID        | int [int64]     | NYP Work ID                        |
| MovementID    | float [float64] | NYP Movement ID                    |
| ComposerName  | string [object] | Composer: Last name, First name    |
| WorkTitle     | string [object] | TITLE (NYP short titles used)      |
| Movement      | string [object] | Movement title as cataloged by NYP |
| ConductorName | string [object] | Conductor: Last name, First name   |
| Interval      | string [object] | Interval tag                       |

### Soloists

| Variable          | Type [dtype]    | Meaning                                                         |  
| :-----------------|:----------------| :---------------------------------------------------------------|
| GUID              | string [object] | Leon Levy Digital Archives ID                                   |
| ProgramID         | int [int64]     | Local NYP ID                                                    |
| WorkID            | int [int64]     | NYP Work ID                                                     |
| MovementID        | float [float64] | NYP Movement ID                                                 |
| SoloistName       | string [object] | Soloist: Last name, First name                                  |
| SoloistInstrument | string [object] | Soloist instrument played, singing voice or type of performance |
| SoloistRole       | string [object] | "S" means "Soloist"; "A" means "Assisting Artist"               |
