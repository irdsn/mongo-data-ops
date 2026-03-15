# MongoDataOps Architecture

## Project Structure

```bash
mongo-data-ops/
├── docs/                                    # Extended project documentation
│   ├── images/                              # Images used in documentation
│   │   └── MongoDB_logo.png                 # MongoDB logo used in docs
│   └── ARCHITECTURE.md                      # Detailed repository structure and script overview
│
├── dups_analysis/                           # Output folder for duplicate analysis results
│   ├── duplicated_ids_to_delete.txt         # IDs marked for deletion
│   ├── duplicates.json                      # Grouped duplicate records
│   └── stats.txt                            # Summary statistics report
│
├── inputs/                                  # Input inputs files for processing
│   ├── ids.txt                              # List of MongoDB _id values
│   └── input_data.json                      # Sample documents for analysis
│
├── scripts/                                 # Automation and inputs operation scripts
│   ├── add_fields.py                        # Adds or updates fields in documents
│   ├── copy_field_by_ids.py                 # Copies a field between collections using a list of _id
│   ├── count_documents.py                   # Efficiently counts documents matching a query
│   ├── count_duplicated.py                  # Detects duplicates in a JSON file based on a field
│   ├── create_docs_with_selected_fields.py  # Creates documents using selected fields only
│   ├── delete_documents_by_ids.py           # Deletes documents from a collection by _id list
│   ├── mark_duplicates_by_field.py          # Flags documents as duplicated based on field comparison
│   ├── remove_fields.py                     # Removes specified fields from documents
│   ├── rename_fields.py                     # Renames fields in MongoDB documents
│   ├── transfer_documents.py                # Transfers documents between collections (by query)
│   ├── transfer_documents_by_ids.py         # Transfers documents between collections (by _id list)
│   ├── update_field.py                      # Updates a single field value in matched documents
│   └── update_fields_from_source.py         # Updates selected fields in target collection using source
│
├── utils/                                   # Utility modules
│   ├── database_connections.py              # Context-managed MongoDB connector
│   └── logs_config.py                       # Centralized color-coded logger setup
│
├── requirements.txt                         # Python dependencies list
├── .env.example                             # Template for MongoDB credentials
├── .gitignore                               # Files and folders to ignore in Git
└── README.md                                # Project documentation
```

## Script Overview

| Script                                        | Purpose                                                                                                   |
|:----------------------------------------------|:----------------------------------------------------------------------------------------------------------|
| `scripts/add_fields.py`                       | Add or update predefined fields with default values in documents matching a query.                        |
| `scripts/copy_field_by_ids.py`                | Copy a specific field from a source collection to a target collection using `_id` values from a file.     |
| `scripts/count_documents.py`                  | Efficiently count documents that match a query using projection-only cursor to avoid timeouts.            |
| `scripts/count_duplicated.py`                 | Detect duplicate values in a local JSON file based on a configurable field and generate deletion reports. |
| `scripts/create_docs_with_selected_fields.py` | Transfer only selected fields from documents in one collection to another, skipping existing ones.        |
| `scripts/delete_documents_by_ids.py`          | Permanently delete documents from a MongoDB collection based on `_id` values provided in a text file.     |
| `scripts/mark_duplicates_by_field.py`         | Flag documents in a source collection as duplicates if a field matches values in a target collection.     |
| `scripts/remove_fields.py`                    | Remove one or more specified fields from all documents that match a given query.                          |
| `scripts/rename_fields.py`                    | Rename fields in documents, preserving the original order or moving renamed fields to the end.            |
| `scripts/transfer_documents.py`               | Copy or move documents between collections based on a query, with batch processing and parallelism.       |
| `scripts/transfer_documents_by_ids.py`        | Copy or move documents from one collection to another using a list of `_id` values from a text file.      |
| `scripts/update_field.py`                     | Update a specific field (and optionally a timestamp) for all documents that match a condition.            |
| `scripts/update_fields_from_source.py`        | Update selected fields in a target collection using matching `_id` documents from a source collection.    |
| `utils/database_connections.py`               | Context-managed MongoDB connection handler. Includes helpers for querying and updating with retry logic.  |
| `utils/logs_config.py`                        | Centralized logging configuration with color-coded console output for INFO, DEBUG, and ERROR levels.      |

> **Note:** Scripts use controlled multithreading, batch sizes, and robust MongoDB connection management.
