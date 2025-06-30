Day 4: Diving Deeper into Bash Scripting
Today was all about getting hands-on with Bash scripting! From basic commands to more complex logical constructs and functions, I explored how to automate tasks and make my command-line experience even more powerful.

Core Concepts & Basic Structure
Bash scripts are essentially lists of commands that the Bash interpreter executes. They're incredibly useful for automating repetitive tasks, managing files, and even building small applications.

The Shebang Line: #!/bin/bash
This is always the first line of a Bash script. It tells the system which interpreter to use to execute the script. #!/bin/bash is the most common for Bash scripts.

Comments: #
Anything after a # on a line is ignored by the interpreter. Use them generously to explain your code!

Executing a Script
Make it Executable: chmod +x your_script.sh

Run it: ./your_script.sh

1. The echo Command & Variables
The echo command is your best friend for displaying output. Variables allow you to store and manipulate data within your scripts.

Basic echo
Bash

#!/bin/bash
echo "Hello, Bash Scripting!"
Working with Variables
Assigning: VARIABLE_NAME="value" (no spaces around =)

Accessing: $VARIABLE_NAME

Read-only: readonly VARIABLE_NAME (prevents reassignment)

Unset: unset VARIABLE_NAME (removes a variable)

Advanced Uses & Daily Notes:
Colored Output: Use ANSI escape codes with echo -e for visual feedback in your scripts. This is fantastic for status messages (e.g., green for success, red for error).

Bash

#!/bin/bash
echo -e "\e[32mSUCCESS: Operation completed!\e[0m" # Green text
echo -e "\e[31mERROR: Something went wrong.\e[0m"   # Red text
Debugging with echo: Sprinkle echo statements throughout your script to see the value of variables at different points. This is a simple but effective debugging technique.

Bash

#!/bin/bash
my_var="initial"
echo "DEBUG: my_var is $my_var"
my_var="changed"
echo "DEBUG: my_var is now $my_var"
Variable Expansion Modifiers:

${VAR:-default}: Use default if VAR is unset or null. Useful for providing fallback values.

${VAR:=default}: Similar, but also assigns default to VAR if unset/null.

${VAR:?error_message}: If VAR is unset/null, print error_message and exit. Critical for mandatory variables.

${#VAR}: Get the length of the string in VAR.

${VAR/pattern/replacement}: Replace the first occurrence of pattern with replacement.

${VAR//pattern/replacement}: Replace all occurrences.

2. Printing User Information (Name, Age, City)
This simple script demonstrates taking user input and displaying it.

Bash

#!/bin/bash
read -p "Enter your name: " name
read -p "Enter your age: " age
read -p "Enter your city: " city

echo "Hello, $name!"
echo "You are $age years old and live in $city."
Advanced Uses & Daily Notes:
Secure Input: For sensitive information (like passwords), use read -s to suppress echoing the input to the screen.

Bash

#!/bin/bash
read -sp "Enter your password: " password
echo # Newline after password input
echo "Password entered (for demonstration): $password"
Timeout for Input: Use read -t SECONDS to set a timeout for user input. If the user doesn't respond within the given time, the script can proceed with a default or error.

Bash

#!/bin/bash
echo "You have 5 seconds to enter your favorite color:"
read -t 5 fav_color

if [ -z "$fav_color" ]; then
    echo "No color entered within 5 seconds. Defaulting to Blue."
    fav_color="Blue"
fi
echo "Your favorite color is: $fav_color"
Reading Multiple Inputs on One Line:

Bash

#!/bin/bash
read -p "Enter name and age (e.g., John 30): " name age
echo "Name: $name, Age: $age"
3. Simple Calculator
Arithmetic in Bash is primarily done using (()) or expr.

Bash

#!/bin/bash
read -p "Enter first number: " num1
read -p "Enter second number: " num2

sum=$((num1 + num2))
difference=$((num1 - num2))
product=$((num1 * num2))
quotient=$((num1 / num2)) # Integer division

echo "Sum: $sum"
echo "Difference: $difference"
echo "Product: $product"
echo "Quotient: $quotient"
Advanced Uses & Daily Notes:
Floating Point Arithmetic: Bash natively only supports integer arithmetic. For floating-point, you need external tools like bc (basic calculator).

Bash

#!/bin/bash
read -p "Enter first decimal number: " dec1
read -p "Enter second decimal number: " dec2

# Use 'bc -l' for floating point arithmetic
result=$(echo "$dec1 + $dec2" | bc -l)
echo "Decimal Sum: $result"

# Set precision for 'bc'
result=$(echo "scale=4; $dec1 / $dec2" | bc -l)
echo "Decimal Quotient (4 decimal places): $result"
Error Handling (Input Validation): Ensure user input is actually a number.

Bash

#!/bin/bash
read -p "Enter a number: " num
if ! [[ "$num" =~ ^[0-9]+$ ]]; then
    echo "Error: '$num' is not a valid number."
    exit 1 # Exit with an error status
fi
echo "You entered a valid number: $num"
Increment/Decrement Shorthand: ((num++)) ((num--)) ((num+=5)) are more efficient than num=$((num + 1)).

4. Comparison of Two Numbers
Use [[ ... ]] for conditional expressions, especially with if statements.

Bash

#!/bin/bash
read -p "Enter first number: " num1
read -p "Enter second number: " num2

if [[ "$num1" -eq "$num2" ]]; then
    echo "$num1 is equal to $num2"
elif [[ "$num1" -gt "$num2" ]]; then
    echo "$num1 is greater than $num2"
else
    echo "$num1 is less than $num2"
fi
Common Comparison Operators:
Numeric:

-eq: Equal to

-ne: Not equal to

-gt: Greater than

-ge: Greater than or equal to

-lt: Less than

-le: Less than or equal to

String:

== or =: Equal to

!=: Not equal to

<: Less than (alphabetical order)

>: Greater than (alphabetical order)

-z: String is null (zero length)

-n: String is not null (non-zero length)

Advanced Uses & Daily Notes:
Logical Operators: Combine conditions using && (AND) and || (OR).

Bash

#!/bin/bash
read -p "Enter a number: " num

if [[ "$num" -gt 0 && "$num" -lt 10 ]]; then
    echo "Number is between 1 and 9."
elif [[ "$num" -ge 100 || "$num" -lt 0 ]]; then
    echo "Number is either 100 or greater, or less than 0."
else
    echo "Number is not in the specified ranges."
fi
Regex Matching: Use =~ for regular expression matching within [[ ]]. This is incredibly powerful for validating inputs or parsing text.

Bash

#!/bin/bash
read -p "Enter an email address: " email

if [[ "$email" =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
    echo "Valid email address."
else
    echo "Invalid email address."
fi
Case-Insensitive String Comparison: Use nocasematch option.

Bash

#!/bin/bash
shopt -s nocasematch # Enable case-insensitive matching
string1="Hello"
string2="hello"

if [[ "$string1" == "$string2" ]]; then
    echo "'$string1' and '$string2' are equal (case-insensitive)."
fi
shopt -u nocasematch # Disable
5. Number Sign Check (Positive, Negative, Zero)
Another application of conditional logic.

Bash

#!/bin/bash
read -p "Enter a number: " num

if [[ "$num" -gt 0 ]]; then
    echo "$num is greater than zero (positive)."
elif [[ "$num" -lt 0 ]]; then
    echo "$num is less than zero (negative)."
else
    echo "$num is equal to zero."
fi
Advanced Uses & Daily Notes:
Using test Command: The [[ ... ]] syntax is a modern Bash extension. The older, POSIX-compliant way is using the test command or single brackets [ ]. While [[ ]] is generally preferred in Bash for its extended features, it's good to be aware of [ ].

Bash

#!/bin/bash
num=5
if [ "$num" -gt 0 ]; then # Note the spaces around the brackets and operators
    echo "Positive (using [ ])"
fi
Ternary Operator (Simulated): While Bash doesn't have a direct ternary operator, you can simulate it with && and ||.

Bash

#!/bin/bash
num=10
result=$(( num > 5 ? 1 : 0 )) # Not direct Bash; this is for contexts like arithmetic
# More Bash-idiomatic:
[[ $num -gt 5 ]] && echo "Greater than 5" || echo "Not greater than 5"
6. While Loop (Decreasing Numbers)
Loops are essential for repetitive tasks. while loops continue as long as a condition is true.

Bash

#!/bin/bash
counter=10

echo "Decreasing numbers:"
while [[ $counter -ge 0 ]]; do
    echo "$counter"
    ((counter--)) # Decrement counter
    sleep 0.5    # Pause for half a second (demonstration)
done
echo "Blast off!"
Advanced Uses & Daily Notes:
break and continue:

break: Exits the loop immediately.

continue: Skips the rest of the current iteration and goes to the next.

Bash

#!/bin/bash
i=0
while [[ $i -lt 10 ]]; do
    ((i++))
    if [[ $i -eq 5 ]]; then
        echo "Skipping 5..."
        continue # Skip print for 5
    fi
    if [[ $i -eq 8 ]]; then
        echo "Breaking at 8..."
        break    # Exit loop
    fi
    echo "Current number: $i"
done
Infinite Loops: while true; do ... done is a common pattern for daemons or services that run continuously. Remember to include a mechanism to exit (e.g., ctrl+c or a specific condition).

Reading from a File Line by Line: A very common and powerful while loop pattern.

Bash

#!/bin/bash
echo "Line 1" > my_file.txt
echo "Line 2" >> my_file.txt
echo "Line 3" >> my_file.txt

echo "Reading file contents:"
while IFS= read -r line; do
    echo "Processing: $line"
done < my_file.txt # Redirects my_file.txt as input to the while loop
# IFS= read -r ensures proper handling of spaces and backslashes
7. While Loop (Increasing Numbers)
Similar to decreasing, just change the condition and increment.

Bash

#!/bin/bash
counter=1

echo "Increasing numbers:"
while [[ $counter -le 5 ]]; do
    echo "$counter"
    ((counter++)) # Increment counter
done
echo "Loop finished."
Advanced Uses & Daily Notes:
Looping with until: The until loop executes commands as long as the condition evaluates to false.

Bash

#!/bin/bash
count=10
until [[ $count -eq 0 ]]; do
    echo "Countdown: $count"
    ((count--))
done
echo "Lift off!"
Waiting for a Resource: Use while loops to wait for a file to appear, a service to start, or a port to be open.

Bash

#!/bin/bash
FILE="/tmp/my_signal_file.txt"
echo "Waiting for $FILE to exist..."
while [[ ! -f "$FILE" ]]; do
    sleep 1
done
echo "$FILE found! Proceeding..."
rm "$FILE" # Clean up
8. For Loop
for loops are excellent for iterating over lists of items or a range of numbers.

Iterating over a sequence (brace expansion):
Bash

#!/bin/bash
echo "Numbers from 1 to 5:"
for i in {1..5}; do
    echo "Number: $i"
done
Iterating over an array (more advanced):
Bash

#!/bin/bash
my_fruits=("Apple" "Banana" "Cherry" "Date")

echo "My favorite fruits:"
for fruit in "${my_fruits[@]}"; do
    echo "- $fruit"
done
C-style for loop (similar to C/Java):
Bash

#!/bin/bash
echo "C-style for loop:"
for (( i=0; i<3; i++ )); do
    echo "Iteration: $i"
done
Advanced Uses & Daily Notes:
Looping through Files/Directories:

Bash

#!/bin/bash
echo "Listing .txt files in current directory:"
for file in *.txt; do
    if [[ -f "$file" ]]; then # Check if it's a regular file
        echo "Found text file: $file"
    fi
done

echo "Listing directories:"
for dir in */; do # Trailing slash for directories
    if [[ -d "$dir" ]]; then
        echo "Found directory: $dir"
    fi
done
Processing Command Line Arguments: The special variables $@ or $* hold all command-line arguments.

Bash

#!/bin/bash
echo "Processing arguments:"
for arg in "$@"; do
    echo "Argument: $arg"
done
# Run as: ./myscript.sh file1.txt doc.pdf image.png
Piping Output to a Loop:

Bash

#!/bin/bash
echo "Processing lines from 'ls -l':"
ls -l | while IFS= read -r line; do
    echo "Line: $line"
done
9. Menu-Driven Calculator using case
The case statement is a cleaner alternative to multiple if/elif/else statements for handling different choices.

Bash

#!/bin/bash

while true; do
    echo "--- Calculator Menu ---"
    echo "1. Addition"
    echo "2. Subtraction"
    echo "3. Multiplication"
    echo "4. Division"
    echo "5. Exit"
    read -p "Enter your choice (1-5): " choice

    case $choice in
        1)
            read -p "Enter first number: " n1
            read -p "Enter second number: " n2
            echo "Result: $((n1 + n2))"
            ;;
        2)
            read -p "Enter first number: " n1
            read -p "Enter second number: " n2
            echo "Result: $((n1 - n2))"
            ;;
        3)
            read -p "Enter first number: " n1
            read -p "Enter second number: " n2
            echo "Result: $((n1 * n2))"
            ;;
        4)
            read -p "Enter first number: " n1
            read -p "Enter second number: " n2
            if [[ $n2 -eq 0 ]]; then
                echo "Error: Division by zero!"
            else
                echo "Result: $((n1 / n2))"
            fi
            ;;
        5)
            echo "Exiting calculator. Goodbye!"
            exit 0 # Exit successfully
            ;;
        *)
            echo "Invalid choice. Please enter a number between 1 and 5."
            ;;
    esac
    echo # Newline for readability
done
Advanced Uses & Daily Notes:
Pattern Matching in case: You can use wildcards (globs) in case patterns.

Bash

#!/bin/bash
read -p "Enter a character: " char
case "$char" in
    [a-z]) echo "Lowercase letter";;
    [A-Z]) echo "Uppercase letter";;
    [0-9]) echo "Digit";;
    *)     echo "Special character or symbol";;
esac
Multiple Patterns for One Action: Separate patterns with |.

Bash

#!/bin/bash
read -p "Enter a day of the week: " day
case "$day" in
    Monday|Tuesday|Wednesday|Thursday|Friday)
        echo "It's a weekday."
        ;;
    Saturday|Sunday)
        echo "It's a weekend!"
        ;;
    *)
        echo "Not a valid day."
        ;;
esac
Implementing Complex Workflows: case statements are excellent for building interactive scripts or handling different execution paths based on command-line arguments.

10. String Manipulation (Length, Uppercase, Lowercase, First Upper)
Bash offers powerful built-in string manipulation.

Bash

#!/bin/bash
word="hello world"

# Length
echo "Original word: '$word'"
echo "Length: ${#word}"

# Uppercase
echo "Uppercase: ${word^^}"

# Lowercase
echo "Lowercase: ${word,,}"

# Capitalize first letter (Bash 4+ specific)
echo "First letter capitalized: ${word^}"

# Replace substring
echo "Replace 'world' with 'bash': ${word/world/bash}"

# Substring extraction
echo "Substring (from index 6, length 5): ${word:6:5}"
Advanced Uses & Daily Notes:
Parameter Expansion for Substring Removal:

${VAR#pattern}: Remove shortest matching pattern from the beginning.

${VAR##pattern}: Remove longest matching pattern from the beginning.

${VAR%pattern}: Remove shortest matching pattern from the end.

${VAR%%pattern}: Remove longest matching pattern from the end.

Bash

#!/bin/bash
filename="archive.tar.gz"
echo "Full filename: $filename"
echo "Extension removed (shortest): ${filename%.*}" # archive.tar
echo "Extension removed (longest): ${filename%%.*}" # archive

path="/home/user/documents/report.pdf"
echo "Full path: $path"
echo "Filename only: ${path##*/}"         # report.pdf
echo "Directory only: ${path%/*}"         # /home/user/documents
Array Manipulation: While not directly string manipulation, often goes hand-in-hand.

${ARRAY[@]}: All elements

${ARRAY[0]}: First element

${#ARRAY[@]}: Number of elements

ARRAY+=("new_item"): Add element

11. Functions
Functions allow you to modularize your code, making it more organized, readable, and reusable.

Bash

#!/bin/bash

# Define a simple function
greet() {
    echo "Hello from the greet function!"
}

# Function with arguments
add_numbers() {
    local num1=$1 # Access arguments using $1, $2, etc.
    local num2=$2
    local sum=$((num1 + num2)) # 'local' creates a local variable, good practice
    echo "The sum of $num1 and $num2 is: $sum"
    return 0 # Functions can return an exit status (0 for success)
}

# Function with return value (via echo and command substitution)
get_current_time() {
    date +"%H:%M:%S"
}

# Call the functions
greet
add_numbers 10 20

current_time=$(get_current_time) # Capture output of function
echo "Current time: $current_time"

# Check function's exit status
if add_numbers 5 7; then
    echo "Addition successful."
else
    echo "Addition failed."
fi
Advanced Uses & Daily Notes:
Return Values vs. Echoing Output: Functions return an exit status (0 for success, non-zero for error), but they output data to stdout. To get data from a function, capture its stdout using command substitution ($(function_name)).

Variable Scope (local): Always use local for variables inside functions unless you explicitly intend for them to be global. This prevents unintended side effects and makes your functions more predictable.

Error Handling in Functions: Functions can return non-zero exit codes to indicate failure, which can then be checked by the calling script.

Bash

#!/bin/bash
validate_input() {
    local input="$1"
    if [[ -z "$input" ]]; then
        echo "Error: Input cannot be empty." >&2 # Redirect error to stderr
        return 1 # Indicate failure
    fi
    return 0 # Indicate success
}

if validate_input ""; then
    echo "Input was valid."
else
    echo "Input was invalid, script continuing with caution."
fi
Exporting Functions: If you want a function to be available in subshells (e.g., when running another script from within your script), you can export -f function_name.

12. Checking if a File Exists
File system checks are fundamental in Bash scripting.

Bash

#!/bin/bash
read -p "Enter a filename: " filename

if [[ -f "$filename" ]]; then
    echo "'$filename' is a regular file and exists."
elif [[ -d "$filename" ]]; then
    echo "'$filename' is a directory and exists."
else
    echo "'$filename' does not exist or is neither a file nor a directory."
fi
Common File Test Operators:
-f FILE: True if FILE is a regular file.

-d DIR: True if DIR is a directory.

-e PATH: True if PATH exists (file, directory, link, etc.).

-s FILE: True if FILE exists and has a size greater than zero.

-r FILE: True if FILE exists and is readable.

-w FILE: True if FILE exists and is writable.

-x FILE: True if FILE exists and is executable.

-L FILE: True if FILE is a symbolic link.

FILE1 -nt FILE2: True if FILE1 is newer than FILE2.

FILE1 -ot FILE2: True if FILE1 is older than FILE2.

Advanced Uses & Daily Notes:
Creating Files/Directories Conditionally:

Bash

#!/bin/bash
if [[ ! -d "my_logs" ]]; then
    mkdir my_logs
    echo "Created 'my_logs' directory."
fi

if [[ ! -f "my_logs/today.log" ]]; then
    touch my_logs/today.log
    echo "Created 'my_logs/today.log'."
fi
Checking for Permissions Before Actions: Always check if a script has the necessary permissions before attempting file operations to provide more user-friendly error messages.

Bash

#!/bin/bash
log_file="/var/log/my_app.log" # Often requires root permissions

if [[ ! -w "$log_file" ]]; then
    echo "Error: Cannot write to $log_file. Check permissions." >&2
    exit 1
fi
echo "Logging to $log_file..."
# echo "This is a log entry." >> "$log_file"
find Command for Complex Searches: For more sophisticated file searches (by name, size, type, age, etc.), combine find with your scripts.

Bash

#!/bin/bash
echo "Finding files larger than 1MB:"
find . -type f -size +1M -print
