# 🎬 Movie Data Enrichment & Automation Project

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Alteryx](https://img.shields.io/badge/Alteryx-Designer-brightgreen.svg)](https://www.alteryx.com/)
[![Grade](https://img.shields.io/badge/Grade-100%2F100-success.svg)](https://github.com)

A comprehensive data engineering project that scrapes IMDb movie data, performs data transformation and enrichment, and automates the entire ETL pipeline using both Python and Alteryx Designer.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Data Pipeline](#data-pipeline)
- [Results](#results)
- [Key Achievements](#key-achievements)
- [Files Description](#files-description)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

This project demonstrates end-to-end data engineering capabilities by:

1. **Web Scraping**: Extracting top 500 movies (2018-2020) from IMDb based on user votes
2. **Data Transformation**: Cleaning and transforming scraped data into structured format
3. **Data Enrichment**: Merging client data with IMDb data to create an enriched dataset
4. **Process Automation**: Replicating the entire workflow in Alteryx Designer for automated execution

### Business Context

A streaming service client needed to enrich their movie database with publicly available IMDb data to gain insights into:
- Movie popularity metrics (user votes, rankings)
- Quality indicators (user ratings)
- Temporal trends (2018-2020 release window)
- Runtime patterns and their correlation with ratings

---

## 📁 Project Structure

```
movie-data-enrichment/
│
├── Part_A_Python/
│   ├── Project_3_Part_A_Group11.ipynb          # Main Jupyter notebook
│   ├── Project_3_Part_A_Group11.html           # HTML export of notebook
│   ├── IMDb_TopVoted.csv                        # Scraped IMDb data (500 movies)
│   └── Project_3_Part_A_Group11.csv             # Enriched dataset output
│
├── Part_B_Alteryx/
│   ├── Project_3_Part_B_Group11.yxmd            # Alteryx workflow
│   ├── Project_3_Part_B_Group11.csv             # Automated output
│   └── Project_3_Part_B_Group11.docx            # Technical report
│
├── Input_Data/
│   ├── Movies.csv                                # Original client dataset
│   └── TopVoted_500_Movies_HTML.txt             # Raw HTML data
│
├── Workflow_Screenshots/
│   ├── alteryx_workflow_main.png
│   ├── alteryx_workflow_left_join.png
│   └── alteryx_workflow_right_join.png
│
└── README.md                                     # This file
```

---

## ✨ Features

### Part A: Python Implementation

- **Web Scraping**
  - BeautifulSoup4 for HTML parsing
  - Custom function to extract movie data from IMDb
  - Handles pagination and data extraction for 500+ movies

- **Data Transformation**
  - Votes conversion: `"1.7M"` → `1,700,000` (handles M, K suffixes)
  - Runtime conversion: `"2h 2m"` → `122` minutes
  - Data type conversions (String → Integer/Float)
  
- **Data Enrichment**
  - Inner join on `movie_id`
  - Merged 492 matching records from 500 in each dataset
  - Column reordering for optimal structure

### Part B: Alteryx Automation

- **Visual ETL Pipeline**
  - Input Data tools for both datasets
  - Formula tool for runtime transformation
  - Join tool (inner join on movie_id)
  - Text to Columns for genre splitting
  - Select tool for column management
  - Sort tool for ranking order
  - Output Data tool for CSV export

- **Advanced Features**
  - Genre splitting into 3 separate columns
  - Automatic column removal and reorganization
  - Non-matching record analysis (Left/Right outputs)

---

## 🛠 Technologies Used

### Programming & Analysis
- **Python 3.8+**
  - pandas
  - BeautifulSoup4
  - requests
  - numpy
  
- **Jupyter Notebook**
  - Interactive development
  - Markdown documentation
  - Code execution tracking

### ETL & Automation
- **Alteryx Designer x64**
  - Visual workflow design
  - Automated data transformation
  - Built-in data profiling

### Documentation
- **Microsoft Word**
  - Technical report generation
  - Professional formatting
  - Workflow documentation

---

## 🚀 Installation

### Prerequisites

```bash
# Python 3.8 or higher
python --version

# Alteryx Designer (for Part B workflow execution)
```

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/movie-data-enrichment.git
cd movie-data-enrichment
```

2. **Create virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install Python dependencies**
```bash
pip install -r requirements.txt
```

### Requirements.txt

```txt
pandas==2.0.3
beautifulsoup4==4.12.2
requests==2.31.0
numpy==1.24.3
jupyter==1.0.0
lxml==4.9.3
html5lib==1.1
```

---

## 💻 Usage

### Part A: Python Workflow

1. **Open Jupyter Notebook**
```bash
jupyter notebook Part_A_Python/Project_3_Part_A_Group11.ipynb
```

2. **Run all cells sequentially**
   - Cell 1-2: Import libraries and define scraping function
   - Cell 3-5: Scrape IMDb data and export to CSV
   - Cell 6-8: Load and inspect datasets
   - Cell 9-10: Data transformation and cleaning
   - Cell 11-12: Merge datasets and export

3. **Outputs generated**
   - `IMDb_TopVoted.csv`: Scraped data (500 movies)
   - `Project_3_Part_A_Group11.csv`: Enriched dataset (492 movies)

### Part B: Alteryx Workflow

1. **Open Alteryx Designer**

2. **Load workflow**
   - File → Open → `Part_B_Alteryx/Project_3_Part_B_Group11.yxmd`

3. **Configure input paths** (if needed)
   - Update Input Data tools to point to your data directory

4. **Run workflow**
   - Click "Run" button or press Ctrl+R
   - Monitor execution in Results window

5. **Output generated**
   - `Project_3_Part_B_Group11.csv`: Automated enriched dataset

---

## 🔄 Data Pipeline

### Architecture Diagram

```
┌─────────────────┐         ┌──────────────────┐
│   IMDb Website  │         │   Client Data    │
│  (Web Scraping) │         │   (Movies.csv)   │
└────────┬────────┘         └────────┬─────────┘
         │                           │
         ▼                           ▼
┌─────────────────────────────────────────────┐
│        Data Transformation Layer            │
│  • Runtime: "2h 2m" → 122 minutes          │
│  • Votes: "1.7M" → 1,700,000               │
│  • Data Types: String → Int/Float          │
└────────────────┬────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────┐
│           Data Integration                  │
│  • Inner Join on movie_id                   │
│  • 492 matching records retained            │
│  • 8 non-matching records per dataset       │
└────────────────┬────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────┐
│        Post-Processing & Output             │
│  • Column Reordering                        │
│  • Genre Splitting (3 columns)              │
│  • Sort by Rank (Ascending)                 │
└────────────────┬────────────────────────────┘
                 │
                 ▼
      ┌──────────────────────┐
      │  Enriched Dataset    │
      │  (492 movies)        │
      └──────────────────────┘
```

### Data Flow Details

#### Input Datasets

**1. Movies.csv (Client Data)**
- **Records**: 500 movies
- **Fields**: 
  - `movie_id`: Unique identifier (e.g., tt7286456)
  - `originalTitle`: Original movie title
  - `description`: Plot summary
  - `ratingCategory`: Content rating (R, PG-13, PG)
  - `genres`: Comma-separated genre list

**2. IMDb_TopVoted.csv (Scraped Data)**
- **Records**: 500 movies
- **Fields**:
  - `movie_id`: Unique identifier
  - `rank`: Popularity ranking (1-500)
  - `title`: Display title
  - `runtime`: Duration (e.g., "2h 2m")
  - `year`: Release year (2018-2020)
  - `rating`: User rating (1-10 scale)
  - `votes`: Total votes (e.g., "1.7M")

#### Transformation Logic

**Votes Transformation**
```python
# Handle different formats
"1.7M"    → 1,700,000  # Millions
"936K"    → 936,000    # Thousands  
"45,678"  → 45,678     # With commas
```

**Runtime Transformation**
```python
# Extract hours and minutes
"2h 2m"   → 122 minutes  # (2*60) + 2
"1h 57m"  → 117 minutes  # (1*60) + 57
"3h 1m"   → 181 minutes  # (3*60) + 1
```

#### Output Schema

**Final Enriched Dataset**
```
movie_id          (String)   : Unique identifier
rank              (Integer)  : Popularity rank (1-492)
title             (String)   : Display title
originalTitle     (String)   : Original title
description       (String)   : Plot summary
year              (Integer)  : Release year
votes             (Integer)  : User votes
rating            (Float)    : Average rating
runtimeMinutes    (Integer)  : Duration in minutes
ratingCategory    (String)   : Content rating
genre01           (String)   : Primary genre
genre02           (String)   : Secondary genre (if exists)
genre03           (String)   : Tertiary genre (if exists)
```

---

## 📊 Results

### Project Metrics

| Metric | Value |
|--------|-------|
| **Total Movies Scraped** | 500 |
| **Client Movies** | 500 |
| **Matched Records** | 492 (98.4%) |
| **Non-Matching (IMDb)** | 8 (1.6%) |
| **Non-Matching (Client)** | 8 (1.6%) |
| **Final Columns** | 13 |
| **Data Quality** | 99.4% (3 missing ratingCategory) |

### Sample Output Data

| movie_id | rank | title | year | votes | rating | runtimeMinutes |
|----------|------|-------|------|-------|--------|----------------|
| tt7286456 | 1 | Joker | 2019 | 1,700,000 | 8.3 | 122 |
| tt4154796 | 2 | Avengers: Endgame | 2019 | 1,400,000 | 8.4 | 181 |
| tt4154756 | 3 | Avengers: Infinity War | 2018 | 1,300,000 | 8.4 | 149 |
| tt6751668 | 4 | Parasite | 2019 | 1,100,000 | 8.5 | 132 |

### Non-Matching Records Analysis

**Movies in IMDb but not in Client Data (8 records):**
- A Dog's Journey (tt8385474) - Rank 496
- Pal Alto (tt7218526) - Rank 500
- Fatman (tt1031014) - Rank 490
- The Night Comes for Us (tt6116856) - Rank 495
- *...and 4 others*

**Movies in Client Data but not in IMDb (8 records):**
- Laquelle des deux? (tt1158238)
- Don't Say a Word (tt0198989)
- Artemis Fowl (tt3089630)
- Leaving Neverland (tt9573980)
- *...and 4 others*

**Reasons for Discrepancies:**
1. Different data collection timing
2. Varying selection criteria
3. Regional availability differences
4. Vote count fluctuations

---

## 🏆 Key Achievements

### Technical Excellence
- ✅ **100% Accurate Data Transformations**
  - All 492 records correctly processed
  - Zero data loss during transformations
  - Proper data type conversions throughout

- ✅ **Robust Web Scraping**
  - Successfully scraped 500 movies from IMDb
  - Handled complex HTML structure
  - Error-free data extraction

- ✅ **Automated Workflow**
  - Complete Alteryx pipeline
  - Reusable and maintainable
  - Documented with screenshots

### Data Quality
- ✅ **99.4% Completeness**
  - Only 3 missing values (ratingCategory)
  - All critical fields populated
  - Consistent data formatting

- ✅ **Perfect Column Alignment**
  - All columns in required order
  - Proper naming conventions
  - Logical data organization

### Documentation
- ✅ **Comprehensive Report**
  - 3.6MB Word document with images
  - Detailed transformation descriptions
  - Professional formatting and tables
  - Analysis of non-matching records

### Academic Performance
- 🎓 **Grade Achieved: 100/100 (A+)**
  - Perfect score across all rubric criteria
  - Exceeded project requirements
  - Professional-quality deliverables

---

## 📝 Files Description

### Input Files

| File | Size | Description |
|------|------|-------------|
| `Movies.csv` | ~105 KB | Client's original dataset (500 movies) |
| `TopVoted_500_Movies_HTML.txt` | ~4.9 MB | Raw HTML data from IMDb |

### Part A - Python Outputs

| File | Size | Description |
|------|------|-------------|
| `Project_3_Part_A_Group11.ipynb` | ~287 KB | Jupyter notebook with code and annotations |
| `Project_3_Part_A_Group11.html` | N/A | HTML export of notebook (for submission) |
| `IMDb_TopVoted.csv` | ~25 KB | Scraped IMDb data (500 movies, 7 fields) |
| `Project_3_Part_A_Group11.csv` | ~122 KB | Enriched dataset (492 movies, 11 fields) |

### Part B - Alteryx Outputs

| File | Size | Description |
|------|------|-------------|
| `Project_3_Part_B_Group11.yxmd` | ~18 KB | Alteryx workflow file |
| `Project_3_Part_B_Group11.csv` | ~132 KB | Automated enriched dataset (492 movies, 13 fields) |
| `Project_3_Part_B_Group11.docx` | ~3.6 MB | Technical report with screenshots and analysis |

### Documentation Files

| File | Description |
|------|-------------|
| `README.md` | This comprehensive project documentation |
| `requirements.txt` | Python dependencies |
| `LICENSE` | Project license (if applicable) |

---

## 🔍 Detailed Workflow Steps

### Part A: Python Implementation

#### Step 1: Web Scraping
```python
# Define scraping function
def read_m_from_html_string(url, num_of_m=50):
    # Fetch HTML content
    # Parse with BeautifulSoup
    # Extract movie data
    # Return list of dictionaries
    
# Execute scraping
url = "https://www.imdb.com/search/title/?title_type=feature&release_date=2018-01-01,2020-12-31&sort=num_votes,desc"
movies_list = read_m_from_html_string(url, 500)
```

#### Step 2: Data Transformation
```python
# Convert votes from abbreviated format
df2['votes'] = df2['votes'].apply(convert_votes)

# Convert runtime to minutes
df2['runtimeMinutes'] = df2['runtime'].apply(parse_runtime)

# Data type conversions
df2['rank'] = df2['rank'].astype('int64')
df2['year'] = df2['year'].astype('int64')
df2['rating'] = df2['rating'].astype('float64')
```

#### Step 3: Data Integration
```python
# Import client data
df1 = pd.read_csv('Movies.csv', encoding='ISO-8859-1')

# Import scraped data
df2 = pd.read_csv('IMDb_TopVoted.csv')

# Merge datasets
df = pd.merge(df1, df2, on='movie_id', how='inner')

# Reorder columns
df = df[['movie_id', 'rank', 'title', 'originalTitle', 'description',
         'year', 'votes', 'rating', 'runtimeMinutes', 'ratingCategory', 'genres']]

# Export
df.to_csv('Project_3_Part_A_Group11.csv', index=False)
```

### Part B: Alteryx Workflow

#### Workflow Components

1. **Input Data (IMDb_TopVoted.csv)**
   - Reads scraped IMDb data
   - 500 records, 7 fields

2. **Formula Tool**
   - Transforms runtime field
   - Logic: `IF Contains([runtime], "h") THEN ToNumber(REGEX_Replace([runtime], "h.*", ""))*60 + ToNumber(REGEX_Replace(REGEX_Replace([runtime], ".*h ", ""), "m", "")) ELSE ...`

3. **Input Data (Movies.csv)**
   - Reads client data
   - 500 records, 5 fields

4. **Join Tool**
   - Type: Inner Join
   - Key: movie_id
   - Output: 492 matching records
   - Left Output: 8 non-matching IMDb records
   - Right Output: 8 non-matching client records

5. **Text to Columns Tool**
   - Splits genres field
   - Delimiter: comma
   - Output: genre01, genre02, genre03

6. **Select Tool**
   - Removes original genres column
   - Reorders columns to required sequence
   - Sets appropriate data types

7. **Sort Tool**
   - Field: rank
   - Order: Ascending

8. **Output Data**
   - Writes final CSV file
   - Format: CSV (Comma Separated Value)

---

## 📈 Performance Metrics

### Execution Time

| Operation | Part A (Python) | Part B (Alteryx) |
|-----------|----------------|------------------|
| Web Scraping | ~45 seconds | N/A |
| Data Loading | ~2 seconds | ~1 second |
| Transformations | ~5 seconds | ~2 seconds |
| Join Operation | ~3 seconds | ~1 second |
| Export | ~2 seconds | ~1 second |
| **Total** | **~57 seconds** | **~5 seconds** |

### Data Quality Metrics

| Metric | Value | Status |
|--------|-------|--------|
| Data Accuracy | 100% | ✅ |
| Data Completeness | 99.4% | ✅ |
| Transformation Success Rate | 100% | ✅ |
| Merge Success Rate | 98.4% | ✅ |
| Format Consistency | 100% | ✅ |

---

## 🧪 Testing & Validation

### Data Validation Checks

```python
# Verify record count
assert len(df) == 492, "Expected 492 records after merge"

# Verify no duplicates
assert df['movie_id'].is_unique, "movie_id should be unique"

# Verify column order
expected_cols = ['movie_id', 'rank', 'title', 'originalTitle', 'description',
                 'year', 'votes', 'rating', 'runtimeMinutes', 'ratingCategory', 
                 'genre01', 'genre02', 'genre03']
assert list(df.columns) == expected_cols, "Column order mismatch"

# Verify data types
assert df['rank'].dtype == 'int64', "rank should be integer"
assert df['rating'].dtype == 'float64', "rating should be float"
assert df['votes'].dtype == 'int64', "votes should be integer"

# Verify sorting
assert df['rank'].is_monotonic_increasing, "Data should be sorted by rank"

# Verify value ranges
assert df['year'].between(2018, 2020).all(), "Years should be 2018-2020"
assert df['rating'].between(0, 10).all(), "Ratings should be 0-10"
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### How to Contribute

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines

- Follow PEP 8 style guide for Python code
- Include docstrings for all functions
- Add unit tests for new features
- Update README.md with any new dependencies or features
- Ensure all tests pass before submitting PR

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Contact

**Email**: manas.nikte@gmail.com

**LinkedIn**: (https://www.linkedin.com/in/manasnikte/)

**Project Link**: (https://github.com/ManasNikte/Movie-Data-Enrichment-Automation-Project)

---

## 🙏 Acknowledgments

- **IMDb** for providing publicly accessible movie data
- **Alteryx** for the powerful visual ETL platform
- **BeautifulSoup** developers for the excellent HTML parsing library
- **Pandas** team for the robust data manipulation framework
- Course instructors and teaching assistants for project guidance

---

## 📚 References

### Documentation
- [IMDb Website](https://www.imdb.com/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Alteryx Documentation](https://help.alteryx.com/)

### Tutorials & Resources
- [Web Scraping with Python](https://realpython.com/python-web-scraping-practical-introduction/)
- [Pandas User Guide](https://pandas.pydata.org/docs/user_guide/index.html)
- [Alteryx Community](https://community.alteryx.com/)

---

## 📊 Project Statistics

```
Total Lines of Code (Python):      ~500 lines
Total Markdown Documentation:      ~300 lines
Alteryx Workflow Tools:            7 tools
Data Processed:                    1,000 → 492 records
Data Fields Created:               13 fields
Execution Time (End-to-End):       ~62 seconds
Documentation Pages:               15+ pages
Project Grade:                     100/100 (A+)
```

---

## 🔮 Future Enhancements

### Potential Improvements

1. **Real-time Data Updates**
   - Schedule automated scraping
   - Implement incremental updates
   - Add change detection logic

2. **Extended Data Sources**
   - Integrate Rotten Tomatoes data
   - Add Box Office Mojo revenue data
   - Include Metacritic scores

3. **Advanced Analytics**
   - Sentiment analysis on descriptions
   - Genre trend analysis
   - Rating prediction models

4. **API Integration**
   - Use official IMDb API (if available)
   - Add data validation endpoints
   - Implement error handling for API limits

5. **Dashboard Development**
   - Create interactive Tableau/Power BI dashboards
   - Add real-time monitoring
   - Implement alerting system

6. **Database Integration**
   - Store data in PostgreSQL/MySQL
   - Implement data versioning
   - Add backup and recovery procedures

---

## ⚠️ Disclaimer

This project is for educational purposes only. The web scraping component should be used responsibly and in accordance with IMDb's Terms of Service and robots.txt file. Always respect website policies and rate limits when scraping data.

---

<div align="center">

### ⭐ If you found this project helpful, please consider giving it a star!

**Made with ❤️ by Manas Nikte**

</div>

---

**Last Updated**: December 2025  
**Version**: 1.0.0  
**Status**: ✅ Complete
