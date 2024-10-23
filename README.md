
# Assignmet-4 : File Extraction and Metadata System

## Overview

This project is a Python-based modular system designed to extract **text**, **links**, **images**, and **tables** (along with their metadata) from multiple file formats including **PDF**, **DOCX**, and **PPT**. The extracted data is then stored in various formats, such as files or databases, making it versatile for different use cases. The project is structured using abstract classes to promote flexibility, with concrete implementations for each file type and storage method.

## **Table of Contents**
- [Features](#features)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Testing](#testing)

---

## **Features**

- **File Extraction**: Extracts text, links, images, and tables from PDF, DOCX, and PPT files.
- **Metadata Capture**: Extracts metadata including page numbers, font styles, image resolutions, and table dimensions.
- **Flexible Storage**: Supports saving extracted data either to files (text, CSV, images) or SQL databases.
- **Modular Design**: Abstract classes ensure flexibility, making it easy to extend the project to new file formats or storage systems.
- **Unit Testing**: Includes a robust testing suite for validating functionality across all components.

---

## **Installation**

### **1. Clone the Repository**
To get started, first clone this repository to your local machine:
```bash
git clone https://github.com/yourusername/modular-file-extraction.git](https://github.com/DikshaShorthillsAI/Assignment-4.git
cd Assignment-4
```

### **2. Set Up Python Environment**
It's recommended to create a virtual environment before installing dependencies.

```bash
# Create a virtual environment
python3 -m venv venv

# Activate the virtual environment (Linux/macOS)
source venv/bin/activate

# Activate the virtual environment (Windows)
venv\Scripts\activate
```

### **3. Install Dependencies**
Install the required dependencies using `pip` from the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### **Required Libraries**
- PyPDF2, pdfplumber for handling PDFs.
- python-docx for handling DOCX files.
- python-pptx for handling PPT files.
- Pillow for image handling.
- sqlite3 for SQL-based storage.

---

## **Project Structure**

```
.
├── README.md                       # Documentation
├── requirements.txt                # List of required Python libraries
├── loaders/
│   ├── file_loader.py              # Abstract base class for file loaders
│   ├── concrete_loaders.py         # Loader class for PDF files, DOCX files, PPTX files
│
│   
├── Extractor/
│   └── data_extractor.py           # Data extraction class for text, links, images, and tables
├── Storage/
│   ├── storage.py                  # Abstract base class for storage
│   ├── concrete_storage.py         # Class for saving data to files and SQL database
│ 
├── Test/
│   └── test_suite.py               # Unit tests for extraction and storage
└── script.py                       # Main script for running the extraction process
```

---

## **Usage**

This project allows you to load PDF, DOCX, or PPT files, extract content (text, links, images, tables), and store it either in a file system or an SQLite database.

### 1. Loading a File
The FileLoader abstract class is implemented by concrete classes (PDFLoader, DOCXLoader, PPTLoader). These loaders handle file-specific processing.


### 2. Extracting Data
Use the DataExtractor class to extract text, links, images, and tables from a loaded file. Metadata such as page numbers and image resolution are also captured.

### 3. Saving Data
You can save the extracted data to files or an SQLite database using FileStorage or SQLStorage.

### 4. **Running the Main Script**
You can configure script.py to point to your desired input file and choose your storage method.

```bash
python3 script.py
```

---

## **Testing**

The project includes a comprehensive test suite to validate the functionality of file loading, data extraction, and storage across various file types.

### **Test Cases**
- File validation and loading (PDF, DOCX, PPT).
- Extraction of text, links, images, and tables.
- Verification of metadata extraction (page numbers, resolution, dimensions).
- Storage of data in files and SQL databases.

### **Run Unit Tests**
To run the included tests, use:

```bash
python3 -m unittest Test.test_suite
```
