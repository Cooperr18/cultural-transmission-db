# Cultural Transmission Reference Database

An open-source bibliographic database of academic references on cultural transmission in archaeological research.

## Table of Contents
- [Overview](#overview)
- [Database Contents](#database-contents)
- [Data Formats](#data-formats)
- [Getting Started](#getting-started)
  - [Accessing the Data](#accessing-the-data)
  - [Integration Guide](#integration-guide)
- [Usage Examples](#usage-examples)
- [Contributing](#contributing)
- [Citation](#citation)
- [License](#license)

## Overview

This repository maintains a curated collection of academic references focusing on cultural transmission theory and its applications in archaeology. Designed as a resource for researchers, it provides ready-to-use reference data in multiple formats to support literature reviews, meta-analyses, and research design.

## Database Contents

The database includes:
- Key theoretical works on cultural transmission and archaeology
- Archaeological case studies applying transmission models
- Methodological papers on quantitative approaches
- Interdisciplinary references from anthropology and evolutionary biology
- Annotated entries with key themes and methodologies

## Data Formats

Available in three formats for different research workflows:

1. **CSV** (`references.csv`) - For spreadsheet analysis:
   - Contains all references with standard bibliographic fields
   - Comma-delimited, UTF-8 encoded
   - Column headers: `id,author,title,year,journal,keywords,doi,url`

2. **SQLite** (`cultural_transmission.db`) - For programmatic access:
   - Structured relational database
   - Tables: `references`, `keywords`, `methods`
   - Full-text search enabled

3. **BibTeX** (`references.bib`) - For reference managers:
   - Standard BibTeX format
   - Compatible with Zotero, Mendeley, JabRef, etc.
   - Includes all standard entry types (article, book, etc.)

## Getting Started

### Accessing the Data

1. Clone the repository:
   ```bash
   git clone https://github.com/Cooperr18/cultural-transmission-db.git
   cd cultural-transmission-db/data
   ```

2. Download options:
   - **All formats**: Clone the full repository
   - **Single format**: DOwnload individual files from `data/` directory.
  
### Integration guide

### R:
```r
# Load necessary packages
library(RSQLite)
library(readr)
library(dplyr)

# CSV access
refs_csv <- read_csv("ct_references.csv")

# SQLite access
con <- dbConnect(SQLite(), "ct_references.db")
refs_db <- tbl(con, "references") %>% collect()
```

### Reference Managers:
1. Download `references.bib`
2. Import into your manager (e.g. Zotero, Mendeley Desktop)
3. Organise using the provided keywords

## Usage Examples

### Basic SQL Query in R:
```r
library(DBI)

con <- dbConnect(SQLite(), "ct_references.db")
query <- "
  SELECT title, author, year 
  FROM references 
  WHERE year >= 2015 
  AND keywords LIKE '%pottery%' 
  ORDER BY year DESC
"
results <- dbGetQuery(con, query)
View(results)
```

### CSV Analysis in R:
```r
library(dplyr)
library(ggplot2)

# Load and filter data
refs <- read_csv("ct_references.csv") %>%
  filter(year >= 2010)

# Count publications by year
year_counts <- refs %>%
  count(year, name = "publications")

# Create publication trend plot
ggplot(year_counts, aes(x = year, y = publications)) +
  geom_col(fill = "steelblue") +
  labs(title = "Publications on Cultural Transmission by Year",
       x = "Year",
       y = "Number of Publications") +
  theme_minimal()
```

### BibTeX Citation (RMarkdown):
```r
# Add the chunk-opening ```

{r setup, include=FALSE}
knitr::write_bib(file = "ct_references.bib")


## References
{r refs, echo=FALSE}
bibliography::bibliography("ct_references.bib")
```

## Contributing

We welcome reference additions and corrections:
1. For CSV/BibTeX additions:
   - Add new entries maintaining the same format
   - Include DOI or stable URL when available
   - Provide complete bibliographic information and metadata
   - Abstracts are much appreciated
2. For database updates:
   - Submit the modified `.db` file including SQL scripts for changes
3. Submission process
   ```bash
   fork repository > create branch > add references > submit pull request
   ```

Please include in your pull request:
- Source of new references
- Brief justification for inclusion
- Verification of accuracy

## Citation

When using this database, please cite as:
```text
Author(s). (Year). Cultural Transmission and Archaeology Reference Database.
Version X.X. URL or DOI
```

For example:
```text
Cooper, A. K. (2025). Cultural Transmission and Archaeology Reference Database.
Version 1.0. https://github.com/Cooperr18/cultural-transmission-db
```

## License
This project is licensed under the MIT License -- se the "LICENSE" file for details.

