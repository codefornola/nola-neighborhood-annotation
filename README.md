# NOLA Neighborhood Annotation

I wrote this script after reading [Jeff Asher's blog post](https://nolacrimenews.com/2016/07/30/another-terrific-update-to-data-nola-gov/).
He mentioned that it was hard to segment the call for service data by neighborhood given just the lat, lng.
This script adds a new column to the data with the neighborhood name of the origin call using the neighborhood boundaries
[from this dataset](http://portal-nolagis.opendata.arcgis.com/datasets/e7daa4c977d14e1b9e2fa4d7aff81e59_0.zip).

I have the provided the [annotated 2016 data](data/calls_for_service/2016_annotated.csv) as an example
but this will work with the other years as well. This can also be adapted to work with any type of data.
If you want me to run it on some new data for you, please file file an issue.

## Setup

You'll need `python` and `pip`. This will depend on your system.

Run pip on the requirements file to get the dependencies:

```
pip install -r requirements.txt
```

## Example Usage

The `annotate.py` script takes a csv file for input and outputs a new csv file with the new `Neighborhood` column.
It streams the new rows into the output file one at a time.

```
$ python annotate.py data/calls_for_service/2016.csv output.csv

#2 lat: 29.98645605 lng: -90.06910049 -> FAIRGROUNDS
#3 lat: 29.94662744 lng: -90.06570836 -> CENTRAL BUSINESS DISTRICT
#4 lat: 30.03599373 lng: -89.98642993 -> LITTLE WOODS
#5 lat: 29.94441639 lng: -90.11338583 -> AUDUBON
#6 lat: 29.94556892 lng: -90.09426884 -> CENTRAL CITY
#7 lat: 29.99285922 lng: -90.10284506 -> NAVARRE
#8 lat: 29.95096705 lng: -90.07023215 -> CENTRAL BUSINESS DISTRICT
#9 lat: 30.02696323 lng: -89.95745953 -> READ BLVD EAST
#10 lat: 29.95783188 lng: -90.06637035 -> FRENCH QUARTER
#11 lat: 29.96243871 lng: -90.11365436 -> GERT TOWN
#12 lat: 30.03205044 lng: -89.99409817 -> LITTLE WOODS
#13 lat: 29.95552589 lng: -90.06830144 -> FRENCH QUARTER
#14 lat: 29.97898906 lng: -90.0963655 -> CITY PARK
#15 lat: 30.03610874 lng: -89.9747228 -> READ BLVD EAST
#16 lat: None lng: None -> N/A
#17 lat: 29.97669572 lng: -90.07510558 -> SEVENTH WARD
#18 lat: 29.9617467 lng: -90.11389764 -> GERT TOWN
#.......... Will end when every row is processed
```
