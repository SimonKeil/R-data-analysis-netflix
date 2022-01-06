Untitled
================
Márk Reichmann, Simon Keil, Daniel Henke
6 1 2022

Die Daten sind von
<https://www.kaggle.com/ashishgup/netflix-rotten-tomatoes-metacritic-imdb>

Daten einlesen:

``` r
data <- read_csv("Data/netflix-rotten-tomatoes-metacritic-imdb.csv")
```

    ## Rows: 15480 Columns: 29

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (21): Title, Genre, Tags, Languages, Series or Movie, Country Availabil...
    ## dbl   (7): Hidden Gem Score, IMDb Score, Rotten Tomatoes Score, Metacritic S...
    ## date  (1): Netflix Release Date

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

bisherige Fragestellungen:

*Welches Land hat das beste Netflix?*

filme/Serien getrennt

    Land - einnahmen
          (in welhem Land verdient Netflix am meisten?)
    Sprache - bewerrtungen 
          (in welcher sprache gibt es den höchsten prozentsatz "guter" filme?)
    Land - Anzahl pro Genere
          (gibts mehr deutsche Krimis als Französische?)
    land - Schuspieler
          (sind in jedem land verschiedene Schauspieler beliebt?)
    Land - Sprache 
          (zB Finnland soll keine Synchros machen)

Achtung: Sprache evtl nicht vertrauenswürig

zB hypothesentest: ich glaube, deutschland schaut viele krimis, und
Finnland hat keine übersetzungen

Schätzer für Varianz, Erwartungswert
