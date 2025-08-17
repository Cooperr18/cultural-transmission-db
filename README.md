# CULTURAL TRANSMISSION REFERENCE DATABASE

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
- Key theoretical works on cultural transmission
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
   git clone https://github.com/[your-username]/cultural-transmission-db.git
   cd cultural-transmission-db/data

2. Download options:
   - All formats: Clone the full repository.
   - Single format: Download individual files from `data/` directory.

### Integration guide
#### R:
```
# Load necessary packages
library(RSQLite)
library(readr)
library(dplyr)

# CSV access
refs_csv <- read_csv("references.csv")

# SQLite access
con <- dbConnect(SQLite(), "cultural_transmission.db")
refs_db <- tbl(con, "references") %>% collect()
```

#### Reference Managers:
1. 



   
