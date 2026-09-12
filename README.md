# BINF6250
# Project Title

Homework 1

## Description 

This project consists of 2 functions and 1 main function:

* **read_column(data_file, column_number)**: Takes data file as input and the collumn number analyzed and run the exceptions cases. It takes 2 inputs:
`data_file`: The input needs to be a .txt file.
`column_number`: The column need to be added as integer as input.

* **compute_statistics(values, line_counter, column_number)**: Takes 3 inputs: 
`values`: Those are all values from the column selected .
`line_counter`: The line counter is the a count from all lines of the fil.
`column_number`: The column number is the integer input.

## Getting Started
### Dependencies

* Python 3.12.3
* Standard Libraries: `sys`, `math` 

### Installing 

1. Clone or Download the project files into your local directory.
2. Ensure all three script files are in the same folder:
   * `stats_in_python.py`
   
### Executing Program

To run the function they need to run it on the command line.
The dataset needs to be saved and located on your computer, the column number also need to be added on the input and need to be a integer.

* `stats_in_python.py`


### Help

Issues:
* `Non-Numeric Data`: The script skips lines where the specified column contains strings ot characters cannot be converted to a float.
* `Missing Columns`: If a line is shorter than requested column_number, the scripts exits with an IndexError message to ensure data integrity.
* `Empty Files`: Explains that the script will notify the user if no valid numbers were found in the specified column


### Authors 

Graziano Peregrino 
@graziano_peregrino

### Version History

* 0.1 
  * Initial Release

### License 

This project is licensed under the MIT License - see the LICENSE.md file for details

### Acknowledgments

* BINF6200 Course Materials 
