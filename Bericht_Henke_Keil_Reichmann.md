R-Projekt
================
Márk Reichmann, Simon Keil, Daniel Henke
6 1 2022

Die Daten sind von
<https://www.kaggle.com/ashishgup/netflix-rotten-tomatoes-metacritic-imdb>

Daten einlesen:

``` r
library("tidyverse")
data <- read_csv("Data/netflix-rotten-tomatoes-metacritic-imdb.csv")
```

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

## Explorative Datenanalyse

Zunächst schauen wir uns an, wieviele Filme und Serien es pro Land gibt
und in wievielen Ländern Filme und Serien verfügbar sind.

``` r
colnames(data)
```

    ##  [1] "Title"                 "Genre"                 "Tags"                 
    ##  [4] "Languages"             "Series or Movie"       "Hidden Gem Score"     
    ##  [7] "Country Availability"  "Runtime"               "Director"             
    ## [10] "Writer"                "Actors"                "View Rating"          
    ## [13] "IMDb Score"            "Rotten Tomatoes Score" "Metacritic Score"     
    ## [16] "Awards Received"       "Awards Nominated For"  "Boxoffice"            
    ## [19] "Release Date"          "Netflix Release Date"  "Production House"     
    ## [22] "Netflix Link"          "IMDb Link"             "Summary"              
    ## [25] "IMDb Votes"            "Image"                 "Poster"               
    ## [28] "TMDb Trailer"          "Trailer Site"

``` r
title_country <- data%>%
  select('Country Availability', Title) %>% 
  rename(country = 'Country Availability') %>% 
  separate_rows(country, sep = ",") %>% 
  drop_na()

title_country %>%
  count(country) %>% 
  ggplot(mapping = aes(x = n)) + geom_histogram(bins = 15)
```

![](Bericht_Henke_Keil_Reichmann_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
title_country %>% 
  count(Title) %>% 
  ggplot(mapping = aes(x = n)) + geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Bericht_Henke_Keil_Reichmann_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->
