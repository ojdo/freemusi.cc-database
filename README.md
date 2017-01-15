freemusi.cc-database
====================


Flat tag database file taken from [freemusi.cc](http://freemusi.cc). This file contains years of curating and rating Creative Commons music.

releases.csv
------------

| Column       | Description |
| ------------ | ----------- |
| activity     | *average* of track acitivities (range: 1-3)  |
| album        | **album name**  |
| artist       | **album artist* ("Various Artists" for compilations |
| catalog      | release ID of label ("label123") |
| duration     | *sum* of track lengths (seconds)  |
| genre        | coarse album style (10 keywords) |
| id           | **unique** release ID (identical to URL without common prefix) |
| label        | name of publishing label ("Community  |
| licenseurl   | URL to release license (mainly Creative Commons)  |
| rating       | *average* track ratings (range: 0-5)  |
| style        | fine album style description (tag-like) |
| totaldiscs   | number of discs in release  |
| totaltracks  | number of tracks in release  |
| url          | **URL** to archive.org release page  |
| year         | year of publication  |



tracks.csv
----------
| Column       | Description |
| ------------ | ----------- |
| activity     | mood of track (1=passive, 2=medium, 3=active) |
| disc         | disc number |
| duration     | track length (seconds) |
| id           | **unique** release ID (compare above) |
| rating       | track rating (subjective) |
| title        | **track title** |
| track        | track number |
| trackartist  | track artist name |
| trackurl     |  |


Combined
--------

To combine both, a simple join on track column `id` to the release `id` column is sufficient:

```python
import pandas as pd
releases = pd.read_csv('releases.csv', index_col='id')
tracks = pd.read_csv('tracks.csv')

tracks_w_release_info = tracks.join(releases, on='id')
```

