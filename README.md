# Music Recommendation System

A music recommendation system built using Spotify's Web API, which utilizes both content-based filtering and a hybrid recommendation approach to suggest music based on user input.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Process](#process)
    1. [Data Collection](#data-collection)
    2. [Data Preprocessing](#data-preprocessing)
    3. [Recommendation Algorithms](#recommendation-algorithms)
3. [Results](#results)
4. [Conclusion](#conclusion)

---

## Project Overview

This project leverages the Spotify Web API to create a music recommendation system that can recommend songs based on a given song's audio features and popularity. The system combines **content-based filtering** using features like danceability, energy, and tempo, with a **hybrid model** that adjusts recommendations based on the popularity and release dates of songs.

### Key Features:
- **Content-Based Filtering**: Recommends songs similar to a given input based on their audio features.
- **Hybrid Recommendations**: Enhances the content-based recommendations by factoring in song popularity and release dates.
- **Trending Playlist Data**: Fetches and processes data from trending Spotify playlists, providing detailed information about each track.

---

## Process

### Data Collection

The data for this project is fetched using Spotify’s API, specifically the endpoint for fetching playlist details. The following data points are collected for each track:
- Track name, artists, album name
- Popularity score, release date
- Audio features: Danceability, energy, loudness, speechiness, tempo, etc.

This data is processed to form a structured dataset, which is then used for generating recommendations.

### Data Preprocessing

Once the data is collected, several preprocessing steps are performed:
- **Normalization**: Audio feature data is normalized using MinMaxScaler to bring all values into the range [0, 1].
- **Date Conversion**: Release dates are converted into numerical values to calculate weighted popularity based on recency.
- **Handling Missing Data**: Missing or unavailable data points are handled with default values or ignored during the analysis.

### Recommendation Algorithms

1. **Content-Based Filtering**: 
   - A cosine similarity approach is used to calculate similarity between songs based on their audio features (such as danceability, energy, and loudness).
   - Similar songs are ranked and recommended based on their feature similarity to the input song.

2. **Hybrid Model**:
   - Combines content-based recommendations with a weighted popularity score.
   - Popularity is adjusted by incorporating the recency of the song’s release, giving higher weight to newer songs.
   - The final recommendation list ranks songs by a combination of their content similarity and weighted popularity.

---

## Results

The output of the music recommendation system consists of a list of recommended songs. The system provides a ranked list of songs based on the following criteria:

- **Content-Based Recommendations**: The first set of recommendations will include songs that have the highest similarity in terms of audio features (such as danceability, tempo, and loudness) to the input song. These songs are musically similar and are expected to match the user's taste based on the chosen song’s features.
  
- **Hybrid Recommendations**: The final output merges the content-based results with additional ranking based on the songs' popularity and recency. The hybrid model adjusts the recommendations by weighing more recent and popular songs higher, which can be useful for discovering trending music along with similar tracks.

Thus, the system returns a sorted list of tracks, each with information such as:
- Track name
- Artists
- Album name
- Release date
- Popularity score

The recommendations are displayed in a way that helps users explore music that aligns with their tastes, while also exposing them to new and trending tracks.

---

## Conclusion

The music recommendation system effectively provides personalized song suggestions by using a combination of content-based and hybrid filtering techniques. By leveraging Spotify’s rich track metadata, the system can recommend tracks that not only align with the user’s taste in terms of audio features but also take into account the popularity and freshness of the tracks.

Key takeaways:
- **Content-Based Filtering** allows the system to recommend musically similar tracks.
- **Hybrid Model** improves recommendations by factoring in the recency and popularity of songs.
- The system is flexible and can be easily adapted to different datasets or used with other music APIs for broader recommendations.
