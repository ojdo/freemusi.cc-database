freemusi.cc-database
====================


Flat tag database file recovered from [freemusi.cc](http://freemusi.cc). This file contains years of curating and rating Creative Commons music, all permanently hosted on [The Internet Archive](https://archive.org/details/audio) servers.

releases.csv
------------

| Column       | Description | Unit/Range/Special values/Example  |
| ------------ | ----------- | --------------------- |
| activity     | *average* of track acitivities | range: 1-3 |
| album        | **album name**  |
| artist       | **album artist** | special: "Various Artists" for compilations |
| catalog      | release ID of label | e.g. "BSCOMP0042" |
| duration     | *sum* of track lengths | unit: seconds |
| genre        | coarse album style | remakr: 10 possible values |
| id           | **unique** release ID | remark: identical to url after `details/` |
| label        | name of publishing label | e.g. "Blocsonic" |
| licenseurl   | URL to release license | remark: mainly Creative Commons |
| rating       | *average* track ratings | range: 0-5 |
| style        | fine album style description | remark: tag-like, comma separated |
| totaldiscs   | number of discs in release  | range: 1-10 |
| totaltracks  | number of tracks in release  | range: 1-199 |
| url          | **URL** to release page  | e.g. [archive.org/details/BSCOMP00042](https://archive.org/details/BSCOMP0042) |
| year         | year of publication  | e.g. 2013 |



tracks.csv
----------
| Column       | Description |
| ------------ | ----------- |
| activity     | mood of track (1=passive, 2=medium, 3=active) |
| disc         | disc number |
| duration     | track length (seconds) |
| id           | **unique** release ID (compare above) |
| rating       | track rating (range: 1-5) |
| title        | **track title** |
| track        | track number |
| trackartist  | track artist name |
| trackurl     | direct URL to music file |


Combined
--------

To combine both, a simple join on track column `id` to the release `id` column is sufficient:

```python
import pandas as pd
releases = pd.read_csv('releases.csv', index_col='id')
tracks = pd.read_csv('tracks.csv')

tracks_w_release_info = tracks.join(releases, on='id')
```

License
-------

This dataset is licensed under the [Creative Commons Attribution ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license. Human readable summary:

> ### You are free to:
>   * **Share** — copy and redistribute the material in any medium or format
>   * **Adapt** — remix, transform, and build upon the material for any purpose, even commercially.
>
> The licensor cannot revoke these freedoms as long as you follow the license terms.
>
> ### Under the following terms:
>   * **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
>   * **ShareAlike** — If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
>   * **No additional restrictions** — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.
