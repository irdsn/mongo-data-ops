# MongoDataOps: A clean and modular toolkit for MongoDB data workflows

![Python](https://img.shields.io/badge/Python-3.11-blue.svg)
![Database](https://img.shields.io/badge/Database-MongoDB-green)
![Task](https://img.shields.io/badge/Task-Data_Engineering-orange)
![Last Updated](https://img.shields.io/badge/Last%20Updated-March%202026-brightgreen)

A MongoDB data operations toolkit, born from real-world experience as a Data Engineering Lead & Artificial Intelligence Engineer.

## Table of Contents

- [Introduction](#introduction)
- [Documentation](#documentation)
- [Key Features](#key-features)
- [Installation](#installation)
- [Usage](#usage)
- [Final Words](#final-words)

## Introduction

**MongoDataOps** is a collection of Python scripts designed to automate and streamline frequent data management tasks in MongoDB collections.  

This repository is the result of valuable knowledge and practices acquired during my professional journey. It originated from a position I greatly enjoyed, where I grew extensively both technically and personally.  

The purpose of this repository is to preserve and share that learning, ensuring that the lessons and best practices are never lost.

MongoDataOps aims to provide:
- Efficient, production-grade MongoDB scripts
- Consistency and clarity in database maintenance
- Robust, parallelized, and scalable operations

## Documentation

Additional technical documentation is available in the `/docs` directory.

- **[ARCHITECTURE.md](docs/ARCHITECTURE.md)**  
  Provides a detailed overview of the repository structure, modules, and operational scripts included in the toolkit.

This document explains how the project is organized and how each component contributes to MongoDB data workflows.

## Key Features

- **Batch processing & multithreading**: All scripts are optimized for speed and scalability using batch-based logic and parallel processing.
- **Safe and controlled operations**: Scripts support precise control over field updates, document transfers, deletions, and renaming — with options to preview or limit scope.
- **Duplicate detection & cleansing**: Includes tools to analyze and flag duplicate documents either from local JSON files or between MongoDB collections.
- **Highly modular and configurable**: Configuration is managed through constants in each script, allowing easy adaptation to different datasets or environments.
- **Robust MongoDB integration**: Built-in connection handling via a reusable `MongoDBConnection` class, with support for retries, timeouts, and environment-based credentials.
- **Specialized utilities**:
  - `count_documents.py` uses an optimized projection-based method to handle large collections without timeout issues.
  - `count_duplicated.py` works on local JSON files, offering offline analysis of duplicates.

> ⚠️ **Caution**: Some operations are **destructive** (e.g., deleting or moving documents). Always validate queries and test with small samples before full execution.

## Installation

1. Clone this repository:
```bash
git clone https://github.com/YOUR_USERNAME/mongo-data-ops.git
cd mongo-data-ops
```

2. (Optional but recommended) Create and activate a virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install required Python packages:
```bash
pip install -r requirements.txt
```

## Usage

Each script is standalone and configurable via the constants section at the top of the script.

Example:
```bash
python scripts/add_fields.py
```

Before running a script:
- Review and configure `DATABASE`, `COLLECTION`, `QUERY`, and other parameters.
- Place input files (e.g., `ids.txt`, `input_data.json`) in the `/data` directory.

> Scripts automatically handle logs and progress reporting.

## Contributing & Contact

MongoDataOps isn't just a set of scripts. It's a toolkit born from real data challenges.  
Thank you for checking it out! Hope it saves you time, simplifies your workflows, and sparks new ideas.  
It is an evolving tool, open for experimentation, extension, or integration into larger pipelines.

Feel free to explore, extend, or integrate it into your own applications. Contributions, feedback, or improvements are always welcome.

**If you’ve found this project useful or inspiring — feel free to build on it, break it, or just drop a star ⭐.**

- Bugs / feature requests: please open an **Issue**.
- Direct contact: [inigo.rodsan@gmail.com](mailto:inigo.rodsan@gmail.com)

Developed & maintained by [Íñigo Rodríguez](https://github.com/irdsn).