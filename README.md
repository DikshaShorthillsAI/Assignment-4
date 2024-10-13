
# Assignmet-4 : File Extraction and Metadata System

## Overview

This project is a Python-based modular system designed to extract **text**, **links**, **images**, and **tables** (along with their metadata) from multiple file formats including **PDF**, **DOCX**, and **PPT**. The extracted data is then stored in various formats, such as files or databases, making it versatile for different use cases. The project is structured using abstract classes to promote flexibility, with concrete implementations for each file type and storage method.

## Table of Contents

1. [Features](#features)
2. [Class Structure](#class-structure)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Project Structure](#project-structure)
7. [Testing](#testing)



## Features

- **Multi-format Support**:
  - PDF, DOCX, and PPT file types are supported.
  
- **Data Extraction**:
  - **Text**: Extracts content along with metadata such as page numbers, font styles, and headings.
  - **Links**: Extracts hyperlinks with metadata (linked text, URL, page number).
  - **Images**: Extracts images along with resolution, format, and page number metadata.
  - **Tables**: Extracts tables with information on dimensions and page numbers.

- **Modular Design**:
  - Abstract base classes for flexibility and code reusability.
  - Concrete classes for each file type and storage method.

- **Storage Options**:
  - Store extracted data as CSV files, directories (for images), or in an SQLite database.

## Class Structure

### Abstract Class: FileLoader
- FileLoader: An abstract class that defines methods for validating and loading files.
  - **Concrete Implementations**:
    - PDFLoader: Loads and processes PDF files.
    - DOCXLoader: Loads and processes DOCX files.
    - PPTLoader: Loads and processes PPT files.
    
### DataExtractor Class
- DataExtractor: A class that accepts a FileLoader instance and provides methods to extract data from the file.
  - Methods:
    - extract_text(): Extracts text and metadata.
    - extract_links(): Extracts hyperlinks and metadata.
    - extract_images(): Extracts images and metadata.
    - extract_tables(): Extracts tables and metadata.

### Abstract Class: Storage
- Storage: An abstract class for saving extracted data.
  - **Concrete Implementations**:
    - FileStorage: Saves extracted data as files (text to CSV, images to directories, etc.).
    - SQLStorage: Saves extracted data in an SQLite database.

## Requirements

- Python 3.x
- Required Python packages 

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/DikshaShorthillsAI/Assignment-4.git
   ```
   
2. **Navigate to the project directory**:
   ```bash
   cd Assignment-4
   ```

3. **Install dependencies**:
   Install all required dependencies 

## Usage

1. **Load a File**:
   Choose the file type (PDF, DOCX, or PPT) and use the appropriate loader class (PDFLoader, DOCXLoader, or PPTLoader) to load the file.

2. **Extract Data**:
   Use the DataExtractor class to extract text, links, images, and tables. You can extract specific types of data depending on your needs.
   
   Example:
   ```python
   from concrete_loaders import PDFLoader
   from data_extractor import DataExtractor

   loader = PDFLoader('sample.pdf')
   extractor = DataExtractor(loader)
   text_data = extractor.extract_text()
   links_data = extractor.extract_links()
   images_data = extractor.extract_images()
   tables_data = extractor.extract_tables()
   ```

3. **Save Data**:
   Use the FileStorage or SQLStorage class to store extracted data. You can save the data as CSV files, images to directories, or store everything in an SQLite database.
   
   Example:
   ```python
   from concrete_storage import FileStorage, SQLStorage

   # File storage
   file_storage = FileStorage('output_directory')
   file_storage.save_text_data(text_data, "text_data.csv")
   
   # SQL storage
   sql_storage = SQLStorage('output.db')
   sql_storage.save_text_data(text_data)
   ```

## Testing

A comprehensive test suite is provided to ensure the functionality of all components.

To run the tests:
```bash
python -m unittest test_suite.py
```

### Tests Included:
- **FileLoader Tests**: Validate file loaders for PDF, DOCX, and PPT formats.
- **DataExtractor Tests**: Verify extraction of text, links, images, and tables.
- **Storage Tests**: Ensure correct saving of data to files and databases.
