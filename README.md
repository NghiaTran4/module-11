# module-11
import csv

def write_grades_to_file(file_name):
    # Open the file in write mode
    with open(file_name, 'w') as file:
        # Prompt the user to enter grades
        print("Enter grades (enter -1 to finish):")
        
        # Initialize an empty list to store grades
        grades = []
        
        # Continue prompting until the user enters -1
        while True:
            grade = input("Enter grade: ")
            
            # Check if the user entered -1
            if grade == '-1':
                break
            
            # Append the grade to the list
            grades.append(int(grade))
        
        # Write the grades to the file
        for grade in grades:
            file.write(f"{grade}\n")
    
    print(f"Grades have been written to {file_name}.")

def read_grades_from_file(file_name):
    # Open the file in read mode
    with open(file_name, 'r') as file:
        # Read all the lines from the file
        lines = file.readlines()
        
        # Initialize variables to store total and count
        total = 0
        count = 0
        
        # Display individual grades and calculate total
        print("Individual grades:")
        for line in lines:
            grade = int(line.strip())  # Convert each line to an integer
            print(grade)
            total += grade
            count += 1
        
        # Calculate and display total, count, and average
        average = total / count
        print(f"Total: {total}")
        print(f"Count: {count}")
        print(f"Average: {average}")

def write_student_records_to_csv(file_name):
    # Open the file in write mode with newline='' to prevent extra newline characters
    with open(file_name, 'w', newline='') as file:
        # Create a CSV writer object
        writer = csv.writer(file)
        
        # Prompt the instructor to enter student records
        print("Enter student records (enter 'done' to finish):")
        
        # Continue prompting until the instructor enters 'done'
        while True:
            # Get input from the instructor
            first_name = input("Enter first name: ")
            
            # Check if the instructor entered 'done'
            if first_name.lower() == 'done':
                break
            
            last_name = input("Enter last name: ")
            exam1_grade = int(input("Enter exam 1 grade: "))
            exam2_grade = int(input("Enter exam 2 grade: "))
            exam3_grade = int(input("Enter exam 3 grade: "))
            
            # Write the student record to the CSV file
            writer.writerow([first_name, last_name, exam1_grade, exam2_grade, exam3_grade])
    
    print(f"Student records have been written to {file_name}.")

# Exercise 9.1: Writing grades to a plain text file
write_grades_to_file('grades.txt')

# Exercise 9.2: Reading grades from a plain text file
read_grades_from_file('grades.txt')

# Exercise 9.3: Writing student records to a CSV file
write_student_records_to_csv('grades.csv')
