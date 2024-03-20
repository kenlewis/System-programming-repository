1)//this is a shell script that will enable the user to enter employee name,hours worked and rate per hour.Then calculate the basic pay


#!/bin/bash

# Prompt user for employee name, hours worked, and rate per hour
read -p "Enter employee name: " name
read -p "Enter hours worked: " hours
read -p "Enter rate per hour: " rate

# Calculate basic pay
basic_pay=$(echo "$hours * $rate" | bc)

# Function to calculate tax based on basic pay
calculate_tax() {
    local basic_pay=$1
    if (( $(echo "$basic_pay <= 1000" | bc -l) )); then
        tax=$(echo "0.1 * $basic_pay" | bc)
    elif (( $(echo "$basic_pay <= 2000" | bc -l) )); then
        tax=$(echo "0.2 * $basic_pay" | bc)
    else
        tax=$(echo "0.3 * $basic_pay" | bc)
    fi
    echo $tax
}

# Calculate tax
tax=$(calculate_tax $basic_pay)

# Calculate net pay
net_pay=$(echo "$basic_pay - $tax" | bc)

# Display results
echo "Employee Name: $name"
echo "hours worked: $hours"
echo "rate per hour: $rate"
echo "Basic Pay: $basic_pay"
echo "Tax: $tax"
echo "Net Pay: $net_pay"




2)//this is a c program that opens a file,writes "hello world' to it,reads the conent back,and then prints the read content and finally,close the file.


#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *file_ptr;
    char data[100];

    // Open file in write mode
    file_ptr = fopen("example.txt", "w");
    if (file_ptr == NULL) {
        printf("Error opening file!\n");
        exit(1);
    }

    // Write "Hello World" to the file
    fprintf(file_ptr, "Hello World");

    // Close the file
    fclose(file_ptr);

    // Open the file in read mode
    file_ptr = fopen("example.txt", "r");
    if (file_ptr == NULL) {
        printf("Error opening file!\n");
        exit(1);
    }

    // Read the content from the file
    fgets(data, 100, file_ptr);

    // Print the read content
    printf("Content of file: %s\n", data);

    // Close the file
    fclose(file_ptr);

    return 0;
}




3.)//this is a shell script that will prompt the user to enter the customerID,CustomerName and unitConsumed then calculate the total electricity bill



#!/bin/bash

# prompt the user for customer i9d customer name and unit consumed
read -p "enter customerID: "ID
read -p "customerName: "Name
read -p"UnitConsumed: "Units
#function to calculate the total bills
if (($echo "$units >0&&<=199" | bc)); then
bill=$(echo "ksh 120"
elif (($(echo "units >200&&<400" | bc)); then bill=$(echo "ksh 150"
elif (($echo "$units >=400&&<600" | bc )); then bill=$(echo "ksh 180"
else (($echo "$units >=600" | bc )); then
bill=$(echo "ksh 200"
fi
echo $bill
#display results
echo "customerID:$ID"
echo "customerName:$Name"
echo "unitsConsumed:$units"
echo "Total Billed:$bill"


