# Calculate complexity in each of subway stations at various times

## Introduction

There are three steps to get a population in each of subway stations.

1. Get datasets
2. Preprocess datasets
3. Visualize distribution of population

## Datasets

### Input Datasets

---

① the number of passenger information in Seoul subway station based on an one hour

- structure

| upd_date | line_num | station_name | board_pass_f04_t05 | getoff_pass_f04_t05 | ... |
| -------- | -------- | ------------ | ------------------ | ------------------- | --- |
| 202101   | 1호선    | 동대문       | 542                | 15                  | ... |

> > > **upd_date**: when this information updated.

> > > **line_num**: a Line number of subway station

> > > **station_name** : a name of subway station

> > > board*pass_f *'time*start'* \_t _'time_end'_ : the number of population who get into subway from _'time_start_ to _'time_end'_

> > > getoff*pass_f *'time*start'* \_t _'time_end'_ : the number of population who get off from _'time_start_ to _'time_end'_

address: http://data.seoul.go.kr/dataList/OA-12252/S/1/datasetView.do

by using code, quantitizing the population in each of stations in Seoul

② the location of subway station in Seoul

- structure

| station_name | Latitude  | longitude  |
| ------------ | --------- | ---------- |
| 동대문       | 37.571284 | 127.008981 |

> > > **station_name** : a name of subway station

> > > **Latitude** : the Latitude in each of stations

> > > **longitude** : the longitude in each of stations

### Preprocessed Dataset

---

① the dataset that have two input datasets' informations above the passage.

- structure

| station_name | Latitude  | longitude  | from06_to10 | from10_to14 | ... | from02_to06 |
| ------------ | --------- | ---------- | ----------- | ----------- | --- | ----------- |
| 동대문       | 37.571284 | 127.008981 | 25024.50    | 31739.25    | ... | 3742.75     |

![Preprocessed Dataset.PNG](./Preprocessed Dataset.PNG)

> > > **station_name** : a name of subway station

> > > **Latitude**: the Latitude in each of stations

> > > **longitude** : the longitude in each of stations

> > > **from06_to10** : the population in each of stations from 6AM to 10AM

> > > **from10_to14** : the population in each of stations from 10AM to 02PM

> > > > > > > > > .
> > > > > > > > > .
> > > > > > > > > .

> > > **from02_to06** : the population in each of stations from 02AM to 06AM

### Function

---

- quantize_station_passengers
  > return the **_list_** of tuples which are formed like **_(city name: string, population: int)_** by using pandas
