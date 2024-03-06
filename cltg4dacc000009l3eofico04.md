---
title: "Day 20: Working with Files (CSV, JSON) in Python"
seoTitle: "Working with Files (CSV, JSON) in Python"
seoDescription: "Unlocking Data: Mastering File Handling with Python (CSV, JSON)"
datePublished: Wed Mar 06 2024 18:15:30 GMT+0000 (Coordinated Universal Time)
cuid: cltg4dacc000009l3eofico04
slug: day-20-working-with-files-csv-json-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709745268432/58e7cb3e-c422-45cd-a24f-fbd6e8f52d2e.png
tags: python, json, csv, learninpublic

---

On the twentieth day of my Python learning journey, I delve into the versatile world of file formats such as CSV and JSON. With Python's built-in packages, handling these formats becomes intuitive. Each CSV and JSON, carries its unique utility, making it imperative to grasp their nuances.

### CSV

CSV (Comma-Separated Values) files are extensively utilized for tabular data, where each line denotes a row, and columns are segregated by a delimiter, commonly a comma. Renowned for their simplicity and versatility, CSV files can be effortlessly created, comprehended, and manipulated using various text editors or spreadsheet applications such as Microsoft Excel or Google Sheets.

CSV example:

```sql
Name,Age,Location
Himanshu,20,Rishikesh
Akhil,20,Dehradun
Aman,21,Dehradun
```

Working with CSV:

```sql
import csv

# Example data to write to the CSV file
data = [
    {"Name": "John", "Age": 25, "City": "New York"},
    {"Name": "Alice", "Age": 30, "City": "London"},
    {"Name": "Bob", "Age": 28, "City": "Paris"}
]

# Writing data to CSV file
with open('data.csv', mode='w', newline='') as file:
    writer = csv.DictWriter(file, fieldnames=["Name", "Age", "City"])
    
    # Write header
    writer.writeheader()
    
    # Write data
    for row in data:
        writer.writerow(row)

print("Data written to CSV file successfully!")

# Reading data from CSV file
with open('data.csv', mode='r') as file:
    reader = csv.DictReader(file)
    
    # Displaying data
    print("Data read from CSV file:")
    for row in reader:
        print(row)
```

This code first writes the data stored in the `data` list of dictionaries to a CSV file named `data.csv`. Then, it reads the data from the same CSV file and prints it to the console. The `csv.DictWriter` and `csv.DictReader` classes are used for writing and reading CSV files, respectively, where each row is represented as a dictionary with keys as column headers.

### JSON

JSON (JavaScript Object Notation) is a lightweight data-interchange format that is easy for humans to read and write, and easy for machines to parse and generate. It is based on a subset of the JavaScript programming language, although it is language-independent and can be used with virtually any programming language.

```sql
{
    "name": "himanshu",
    "age": 20,
    "city": "rishikesh",
    "house": 251
}
```

Manipulating JSON file:

```sql
import json

# Example data to write to JSON file
data = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# Writing data to JSON file
with open('data.json', 'w') as file:
    json.dump(data, file)

print("Data written to JSON file successfully!")

# Reading data from JSON file
with open('data.json', 'r') as file:
    loaded_data = json.load(file)
    print("Data read from JSON file:")
    print(loaded_data)
```

You can manipulate the data as Python objects, and then write it back to the JSON file as needed. The `json` module provides flexible functions for handling different types of JSON data and nesting.

### Conclusion

In summary, this blog introduces the essentials of working with CSV and JSON file formats in Python. It emphasizes CSV files' tabular nature and ease of use while highlighting JSON's lightweight and versatile structure. Through concise code examples, readers learn how to manipulate data in both formats, enabling them to efficiently handle various data types and tasks in their Python projects.

Thankyou💕💕