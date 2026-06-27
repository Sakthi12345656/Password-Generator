🔐 Password Generator in C

📌 Project Overview

This project is a simple Password Generator developed in the C programming language. It creates a random password based on user-defined requirements such as password length, inclusion of numeric digits, and special characters.

The program ensures that the first character is always an alphabet, making the generated password more suitable for common password policies while still allowing a mix of characters for improved security.

🎯 Features

User-defined password length.

Option to include numbers.

Option to include special characters.

First character is always an alphabet.

Dynamic memory allocation using malloc().

Random password generation using rand().

Proper memory management using free().

📚 Header Files

#include <stdio.h>

Provides standard input/output functions like printf() and scanf().

#include <stdlib.h>

Provides memory management functions (malloc(), free()) and random number generation (rand(), srand()).

#include <string.h>

Provides string handling functions such as strcat(), strcmp(), and strlen().

#include <time.h>

Used to initialize the random number generator with the current system time.

📝 Variable Declaration

int length;

Stores the desired password length.

char include_numbers[10];
char include_special[10];

Stores the user's response ("yes" or "no") regarding whether numbers and special characters should be included.

🔤 Character Sets

char letters[] = "...";

Contains uppercase and lowercase English alphabets.

char digits[] = "0123456789";

Contains all numeric digits.

char special_chars[] = "...";

Contains commonly used special characters.

📦 Character Pool

char character_pool[200] = "";

This array acts as the master pool from which random characters are selected.

Initially, only alphabets are added.

Depending on the user's choices, numbers and special characters are appended using strcat().

Example:

If user selects:

Numbers → Yes

Special Characters → No


The pool becomes:

abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789

🎲 Random Number Initialization

srand(time(NULL));

Seeds the random number generator using the current time.

Without this line, every execution would generate the same sequence of passwords.

👤 User Input

The program asks for:

Password length

Include numbers?

Include special characters?

Input validation ensures the password length is greater than zero.

🔧 Building the Character Pool

strcat(character_pool, letters);

Adds alphabets first.

If user selects "yes":

strcat(character_pool, digits);

adds numbers.

Similarly,

strcat(character_pool, special_chars);

adds special symbols.

💾 Dynamic Memory Allocation

char *password = malloc((length + 1) * sizeof(char));

Memory is allocated dynamically because the password length is determined at runtime.

+1 reserves space for the null character ('\0').

If allocation fails:

if(password == NULL)

the program exits safely.

🔒 First Character Rule

password[0] = letters[rand() % letters_len];

The first character is selected only from the alphabet array.

This guarantees that every generated password begins with a letter.

Example:

A8#k91

instead of

#A89jk

🎲 Password Generation

for(int i = 1; i < length; i++)

The loop fills the remaining characters.

Each character is selected randomly from the character pool.

password[i] = character_pool[rand() % pool_len];

Here,

rand() generates a random number.

% pool_len ensures the index remains within the array limits.

🏁 String Termination

password[length] = '\0';

Every C string must end with a null character.

This allows functions like printf() to know where the string ends.

📤 Output

printf("Generated Password: %s", password);

Displays the generated password.

Example:

Generated Password:
K9@d2X!mQ

🧹 Memory Cleanup

free(password);

Releases dynamically allocated memory after use.

This prevents memory leaks.

⚙️ Algorithm

1. Initialize the random number generator.


2. Read password length.


3. Ask whether numbers are required.


4. Ask whether special characters are required.


5. Build the character pool.


6. Allocate memory for the password.


7. Set the first character as an alphabet.


8. Generate the remaining characters randomly.


9. Add the null terminator.


10. Display the password.


11. Free allocated memory.

💡 Sample Output

--- Password Generator Project ---

Enter the length of the password: 10

Are numeric characters required? yes

Are special characters required? yes

Generated Password:
R8@kL2#mQ9

🚀 Future Enhancements

Ensure at least one digit and one special character when selected.

Allow users to exclude similar-looking characters (e.g., O, 0, l, 1).

Add password strength evaluation.

Save generated passwords to a file.

Support multiple password generation in a single execution.

Use a cryptographically secure random number generator for stronger security.

📌 Conclusion

This project demonstrates key C programming concepts, including user input handling, string manipulation, conditional logic, dynamic memory allocation, random number generation, loops, and memory management. It serves as a beginner-friendly yet practical example of building a customizable password generator while following good programming practices.
