🎵 Last.fm Music Analytics Dashboard
📌 Project Overview

This project analyzes global music trends using Last.fm data, focusing on track popularity, artist performance, listener behavior, and genre reach.
The data is processed through an ETL pipeline using Python, stored in Google BigQuery, and visualized using Looker Studio.

The dashboard provides insights such as:
- Most played tracks
- Top artists by popularity and listeners
- Genre reach analysis
- Average playcount and listeners

🛠️ Tech Stack
- Python (Data Extraction & Transformation)
- Last.fm API (Data Source)
- Google BigQuery (Data Warehouse)
- Looker Studio (Data Visualization)
- Pandas
- Requests

📊 Data Source
API: Last.fm Public API
Endpoint: chart.getTopTracks
Data Retrieved: Track name, Artist, Playcount, Listeners, Genres (tags), Rank, URL

🔄 Data Pipeline (ETL)
1️⃣ Extract
Data is fetched from the Last.fm API using HTTP requests.
Main extraction function:
get_top_tracks(limit=100, period='overall')
This step retrieves global top tracks and converts the API response into JSON format.
2️⃣ Transform
Data cleaning and transformation steps include:
- Normalizing nested JSON structure
- Converting numeric fields (playcount, listeners)
- Cleaning genre/tag values
- Removing duplicate columns
- Adding metadata (data_type, extracted_at)
- Renaming columns for consistency

Example transformations:
genres → genres_clean
Ensuring correct data types
Dropping unnecessary columns
3️⃣ Load
The cleaned dataset is uploaded to Google BigQuery using:
df_tracks_bq.to_gbq(
    destination_table='data_lastfm_porto2.tracks',
    project_id='portofolio-2-480507',
    if_exists='replace'
)

This allows the data to be queried directly from Looker Studio.

📈 Dashboard Overview (Looker Studio)
The dashboard includes:
- KPI Cards
- Average Playcount
- Average Listeners
- Bar Charts
- Artist Popularity Score
- Top Artists by Listeners
- Most Played Tracks
- Top Genres by Reach
- Interactive Filters
- Track name
- Genre
Dashboard design focuses on:
- Clean layout
- Clear comparisons
- Interactive exploration

🚀 How to Run
- Clone this repository
- Install dependencies: pip install -r requirements.txt
- Add your Last.fm API Key
- Run the notebook to fetch and upload data
- Connect BigQuery table to Looker Studio

🎯 Key Insights
- Popular tracks tend to cluster around specific genres
- A small number of artists dominate listener counts
- Genre reach varies significantly across tags

📌 Notes
This project is for educational and portfolio purposes. Data is retrieved using public API access
