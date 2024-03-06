# [Assignment 4]

## Description
[Module 4]

## Author
[Ramandeep kaur]

## Assignment
[Troubleshooting and Exception Handling: Programming Beyond Expected Results]

## [PiXELL Transaction Report]
[We will use a diverse strategy to improve the quality of the PiXELL Transaction Report. Regular code reviews will be carried out to verify accuracy and compliance with coding standards, emphasizing the proper implementation of exception handling. SonarQube, a static code analysis tool, will be used to uncover potential flaws early on. Thorough unit and integration testing, aided by an automated testing framework, will examine several situations to confirm the program's correctness and detect any weaknesses. Comprehensive documentation, with a focus on inline code comments and external instructions, can help with understanding and resolving issues. Stringent adherence to best standards for exception handling will be maintained, guaranteeing the provision of informative error messages and appropriate logging. CI/CD pipelines automate activities, and performance monitoring tools handle performance-related concerns. The method seeks to ensure the correctness, precision, and robust exception handling in the PiXELL Transaction Report, establishing a strong foundation for high-quality software.]

## Code Modifications
### 5. Implement Exception Handling

[Modified the code in the `pixell_transaction_report.py` program to handle exceptions when the input file cannot be located. A try-block was wrapped around the code responsible for reading the CSV file, and corresponding except blocks were added. If a `FileNotFoundError` occurs, a meaningful error message is printed to the console. An additional except block is included to catch any other unhandled exceptions.]

try:
    with open('ban_data.csv', 'r') as csv_file:
        # existing code...
except FileNotFoundError as e:
    print(f"ERROR: {e} - Input file not found.")
except Exception as e:
    print(f"ERROR: {e}")
    

# Incorporate Data Validation

**Transaction Type Validation:**
   - Added validation for transaction types to ensure they match predefined values.
   - If a transaction type is invalid, the record is marked as an error.

 ### VALIDATION 1 ###
   if transaction_type not in valid_transaction_types:
       valid_record = False
       error_message += f"Invalid transaction type: {transaction_type}. "

**Transaction Amount Validation:**

    - Implemented validation for transaction amounts to handle non-numeric values.
    - If the amount is non-numeric, the record is marked as an error.
    
### VALIDATION 2 ###
    try:
        transaction_amount = float(row[2])
    except ValueError:
        valid_record = False
        error_message += "Non-numeric transaction amount. "

# Collect Invalid Records:

[Records identified as invalid are collected in the rejected_records list.
A tuple containing the record causing the error and the error message is appended to the list.]

else:
    tuple = (),(error_message)
    rejected_records += tuple

### Program throws ZeroDivisionError.
- **Changes Made**:
  - Incremented `transaction_counter` inside the valid record block to fix the ZeroDivisionError.
  - Added a check to ensure `transaction_counter` is not zero before calculating the average transaction amount.
- **Purpose**: Resolved the division by zero error and ensured accurate calculation of the average transaction amount.