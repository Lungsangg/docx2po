

#### 1. Install the Translate Toolkit:

Make sure you have Python installed on your system. Then, you can install the Translate Toolkit using pip:

```
pip install translate-toolkit

```


#### 2. Convert DOCX to plain text:

Assuming you have multiple DOCX files in a directory, you can use a loop in a shell script to convert each file.

Navigate to the directory containing your DOCX files (if they are in a different location).

Create a new shell script (e.g., convert_files.sh) using a text editor or use the terminal to create and edit the script:

```
nano convert_files.sh

```

Inside the script, use a loop to convert each DOCX file to plain text and save them in a separate folder:


```
#!/bin/bash

# Create a directory to store the plain text files
mkdir -p plain_text_files

# Loop through all DOCX files in the current directory and convert them to plain text
for file in *.docx; do
    # Get the file name without the extension
    filename="${file%.docx}"
    # Convert the DOCX file to plain text with Pandoc and save it in the "plain_text_files" folder
    pandoc -s "$file" -t plain -o "plain_text_files/${filename}.txt"
done

```

Save the script by pressing Ctrl+O and then exit the editor by pressing Ctrl+X.

Make the shell script executable:
```
chmod +x convert_files.sh

```

Run the script:

```
./convert_files.sh
```
The plain text files will be saved in a new folder called plain_text_files within the same directory where the script is executed. For example, if you have file1.docx, file2.docx, etc., the script will generate plain_text_files/file1.txt, plain_text_files/file2.txt, etc.



#### 3. Convert plain text to Gettext PO file

1. Open your terminal
2. Navigate to the directory containing the plain text files you want to convert (if they are in a different location).
3. Create a new shell script (convert_to_po.sh) using a text editor:
```
nano convert_to_po.sh

```
4. Inside the script, add the following content:
```
#!/bin/bash

# Create a directory to store the PO files
mkdir -p po_files

# Loop through all plain text files in the current directory and convert them to PO
for file in *.txt; do
    # Get the file name without the extension
    filename="${file%.txt}"
    # Convert the plain text file to PO with txt2po and save it in the "po_files" folder
    txt2po "$file" -o "po_files/${filename}.po"
done

```

Save the script by pressing Ctrl+O and then exit the editor by pressing Ctrl+X.

5. Make the shell script executable:

```
chmod +x convert_to_po.sh

```
6. Run the script:
```
./convert_to_po.sh
```


The script will create a new folder called 'po_files' within the same directory where the script is executed. It will then loop through all the plain text files in the directory, convert them to Gettext PO files using 'txt2po', and save the resulting PO files in the 'po_files' folder.
