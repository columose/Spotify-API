# Cloud-based web-scraping project using Spotify API

## Table of Contents
* [Summary](#Summary)
* [Objective](#Objective)
* [Impact of project](#Impact-of-project)
* [Methods](#Methods)
* [DataFrame appearance](#DataFrame-appearance)
* [Results](#Results)
* [Discussion](#Discussion)
* [Limitations](#Limitations)
* [Python Scripts](#Python-Scripts)
* [Looker Studio Dashboard](#Looker-Studio-Dashboard)


## Summary
* This project scrapes data ***every day*** from the Spotify 'Top-50 Ireland' daily public playlist to compare with data that was scraped from the global annual playlist series 'Top Hits of (selected year)', ranging from 2000 - 2023.
* Data is scraped and cleaned using ***Python scripts*** in Google Colab environment, stored in Google Big Query, and visualised in Google Looker Studio, meaning that ***the entire project is cloud-based***.

## Objective
The objective of this project was to understand what makes a song popular in Ireland ***today***, and how that compares to global trends of the 21st century.

## Impact of project
* This project provides an innovative pipeline for coupling Spotify's Web API to scrape daily data with Google Cloud's services for cloud computing, storage and visualisation.
* The results of this project are informative for those working in the music industry such as musicians, record labels, or radio music selectors.
  - For example, record labels could notice trends in the audio features of popular music today, such as a listener's preference for shorter track duration and higher     tempo. Conseqeuently, record labels could encourage their artists to produce songs which fit the present-day listener's preferences to ensure success with songs       and albums.

## Methods
* Data is scraped everyday from the 'Top-50 Ireland' public playlist using [SpotiPy](https://spotipy.readthedocs.io/en/2.22.1/), a Python library for the Spotify Web API.
* Once the data is scraped and cleaned, it is stored in Google Big Query and visualised in Google Looker Studio, ensuring that the entire project is cloud-based.
* Data was also scraped from yearly Spotify public playlists of the series 'Top Hits of...', ranging from 2000 to 2023, cleaned, stored in Google Big Query, and visualised in Google Looker Studio.
* An interactive dashboard in Looker Studio compares the top tracks of present-day Irish listeners to top tracks of the 21st century in terms of Top songs, Audio features, Top artists, and Top genres.
### Playlist_to_df function
* My [playlist_to_df](https://github.com/columose/Spotify-API/blob/2e8fc433d7c0dc00a598fb1a867ed7e03bf6d87a/functions.ipynb) custom function uses SpotiPy to:
  1. Request data from the given playlist.
  2. Perform a batch request to obtain the genres of the artists in the playlist.
  3. Perform a batch request to obtain the audio features of the tracks in the playlist.
* The function has a limit of extracting 100 songs from Spotify API to ensure that the rate limit isn't passed for requests.

## DataFrame appearance
![Output of df_to_playlist function](https://github.com/columose/Spotify-API/blob/92cbf2579f171d6518156786152c45d29e91fe8c/Images/Spotify_DF.png)

## Results
* The project scrapes daily Irish top chart data and compares with Global yearly top chart data using an interactive dashboard in Looker Studio.
![Image of dashboard](https://github.com/columose/Spotify-API/blob/e21aa0ddf9e8cc5d04097b99a84939ac095d6edf/Images/Spotify%20API%20dashboard.png)
* It is evident that Irish listener's are following global trends in preferring songs with shorter durations and higher tempos to the average of the 21st century.
* Present-day Irish listeners still love music from historic Irish artists such as *The Cranberries*.
* Perhaps ***the most striking finding*** is that the duration of top tracks has been consistently declining, with the mean duration of present-day top tracks being 47 seconds shorter than those of 2000.
* *Rihanna* is arguably the most successful pop artist of the 21st century, with the most tracks entering the 'Top Hits' annual series. She is followed by *Drake*, *Taylor Swift*, *Eminem* and *Calvin Harris*.
* The most popular song of the 21st century is 'Cruel Summer' by *Taylor Swift*.

## Discussion
* The findings of this project can be applied by music industry professionals. As was mentioned in the impact section, record labels could encourage their artists to produce songs that fit the taste of present-day listeners with shorter song durations and higher tempos.

## Limitations
* Spotify discontinued their 'Top Hits of...' public playlist series in 2019. Data from the 'Top tracks of 2020' and 'Top tracks of 2023' were used for their respective years. I opted not to include data for 2021 and 2022 as Spotify has not provided top track playlists for those years. I used linear interpolation to fill in the gaps for the time-series figure, but this is purely for aesthetics and doesn't effect the calculation of metrics.
* An unfortunate limitation of Spotify's web API is that it won't provide data for the stream count of a song. The closest metric is 'Popularity', but that is probably greatly influenced by streams in recent days/weeks.
* Many of Spotify's audio features are arguably unquantifiable (e.g. valence, danceability). As such, I preferred to interpret less abstract metrics such as duration and tempo.

## Python Scripts
All of the processing scripts for this project can be retrieved from the repository. Click on the 'Open in Colab' icon for better legibility, as each notebook cell becomes condensed when copying from Google Colab to Github.

## Looker Studio dashboard
The main findings are summarised using an [interactive dashboard](https://lookerstudio.google.com/reporting/89c6378a-f65c-40d0-b712-72041bbcd563) in Looker Studio.
