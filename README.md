freemusi.cc-database
====================

db.csv
------

Flat tag database file for freemusi.cc. This file is created from within
foobar2000 using the Text Tools component with the following two single line 
(line breaks added manually) title formatting expressions for export:

Track pattern
%_UID%;%ARTIST%;%TITLE%;%ALBUM%;%DATE%;%GENRE%;%STYLE%;%LENGTH_SECONDS%;
%RELEASE%;%PUBLISHER%;%ALBUM ARTIST%;%RATING%;%MOOD%;%TRACKNUMBER%;
%TOTALTRACKS%;%DISCNUMBER%;%TOTALDISCS%;%SOURCE WEBPAGE URL%;%PLAY_COUNT%;
%FIRST_PLAYED%;%LAST_PLAYED%;%PLAY_STAMP%;%TRACK URL%

Group header pattern
UID;Artist Name;Track Title;Album Title;Date;Genre;Style;Length;
Release;Publisher;Album Artist;Rating;Mood;Track Number;
Total Tracks;Disc Number;Total Discs;URL;Play count;
First played;Last played;Play stamp;Track URL

Group footer pattern
-disabled-

Skip dubplicate/repeating lines
-disabled-


**Remark:** The field *Track URL* is only filled for filenames with 
non-matchable structure (e.g. tou273a, tou273b, tou273c, ... where a, b, c 
correspond to tracks 1, 2, 3...). Most Track URLs are automatically
recognised using a soft string matching, mapping the closest string to a
track.

