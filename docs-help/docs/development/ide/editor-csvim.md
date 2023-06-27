---
title: CSVIM Editor
---

CSVIM Editor
===

The CSVIM editor in the Eclipse Dirigible IDE allows you to open, save, delete, and edit the properties of CSV files. Such properties are:

- [Table](#table)
- [Schema](#schema)
- [File path](#file-path)
- [Delimiter](#delimiter)
- [Quote character](#quote-character)
- [Header](#header)
- [Use header names](#use-header-names)
- [Distinguish empty from null](#distinguish-empty-from-null)
- [Version](#version)

### Table
---

  The **Table** input field can contain letters (a-z, A-Z), numbers (0-9), hyphens ("-"), dots ("."), underscores ("_"), and dollar signs ("$").
  
### Schema
---

   The **Schema** input field can contain letters (a-z, A-Z), numbers (0-9), hyphens ("-"), dots ("."), underscores ("_"), and dollar signs ("$").
   
### File path
---
 
   The **File path** input field can contain letters (a-z, A-Z), numbers (0-9), hyphens ("-"), forward slashes ("/"), dots ("."), underscores ("_"), and dollar signs ("$").

   Here’s an example for a correct file path: */workspace/csv/subfolder/bigstats.csv*. In this example, the file path consists of:
   
   - *workspace*
 
     The workspace is the place where you create and manage the artifacts of your application.

   - *csv*

     This is the name of your project.
     
   - *subfolder*

     This is the subfolder that contains the CSV file.

   - *bigstats.csv*
   
     This is the CSV file.
     
   **Note:** If the file path is formatted properly but doesn't exist, you will be able to save the CSVIM file, but you won't be able to open it with the CSV editor. If the file path isn't formatted properly (for example, by having unsupported characters), you won’t be able to save the CSVIM file or open the CSV file.

### Delimiter
---

   The currently supported delimiters are comma (","), tab ("/t"), vertical bar ("|"), semicolon (";"), and number sign or hash ("#").

   **Note:** If you’re trying to use an unsupported character such as "+", "The delimiter is not supported!" warning message will pop up. Nevertheless, you will be able to open the CSV file and save the CSVIM file.

   ![unsupported_characters](https://user-images.githubusercontent.com/20664881/132522169-9a57b186-7dc2-4d05-afb8-99e5b108ff0f.png)

### Quote character
---

   The currently supported quote characters are apostrophe ("‘"), quotation mark ("“"), and number sign or hash ("#").

   **Note:** If you’re trying to use an unsupported character such as "^", "The quote character is not supported!" warning message will pop up. Nevertheless, you will be able to open the CSV file or save the CSVIM file.

### Header
---

   If you select this checkbox, the first line of your CSV file will be treated as a column title or header.
   
### Use header names
---
 
   If you select this checkbox, the first line of the specified CSV file will be interpreted when importing the file. This option will work **only if** you have enabled the "Header" checkbox.
   
### Distinguish empty from null
---
 
   Select this checkbox if you want to make sure that the table-import process interprets correctly all empty values in the CSV file, which is enclosed with the value selected in the **Quote character** dropdown, for example, as an empty space. This ensures that an empty space is imported "as is" into the target table. If the empty space isn't interpreted correctly, it is imported as null.

### Version
---

  You can specify the version of the CSVIM so you can better manage your CSV and database data.



