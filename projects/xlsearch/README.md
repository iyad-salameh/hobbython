This Python script is a graphical application designed to search for a specified keyword across multiple Excel files within the current directory. It presents a user interface (UI) where users can input a search term, which the program then uses to scan all worksheets in each Excel file for that term. If matches are found, the script displays the file name, sheet name, and the row contents in a table format within the UI.

requirements to run the script:

1. Python: A Python interpreter must be installed on the system where the script will run.

2. openpyxl: The openpyxl package, a Python library used to read and write Excel .xlsx/.xlsm files, must be installed.

3. Tkinter: The tkinter library, which is typically included with the standard Python installation, is used for creating the UI. It must be present and functioning on the system.

4. Excel Files: There must be .xlsx files in the same directory as the script for it to search through.

5. Operating System: The script is intended to run on a Windows system, as the UI and file handling are created with Windows conventions in mind. However, tkinter and openpyxl are cross-platform, so the script could potentially be run on other operating systems with little to no modification.

To execute the script, you'd typically navigate to its directory in a command prompt or terminal and run python xlsearch.py
The application window will then open, allowing the user to interact with the application as intended.
