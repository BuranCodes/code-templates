# Code Templates

## **C programming language**

## `Dynamic input string allocation`

This code snippet demonstrates a dynamic allocation technique for reading user input in C. It allows the user to enter text of any length and dynamically expands the memory allocation to accommodate the input.

### **Code Explanation**

1. The initial size of the input string is set to 8 characters (`strsize = 8`), but it can be adjusted as needed.

2. A temporary character array `tmpc` is initialized with a size of 2 to hold the current character and a null terminator.

3. A pointer `input` is declared to store the user input string. It is initially set to `NULL`.

4. Memory is allocated for the input string using `calloc`, with the initial size `strsize` and a size of `char`.

5. The code enters a `while` loop that reads characters from `stdin` until a terminating condition is met.

6. The current character is read using `fgetc(stdin)` and stored in the `tmp` variable.

7. If the character is equal to `EOF` or a newline character (`'\n'`), it is converted to 0 to indicate the end of input.

8. If the length of the input string reaches the current allocation size minus 1 (`strsize-1`), the allocation is expanded.

    - The allocation size is increased by multiplying `strsize` with an expansion factor (`EXPANSION_FACTOR`), which is defined as `1.5` in the code snippet.

    - Memory is reallocated using `realloc` to accommodate the expanded size. If the reallocation fails, an error message is displayed, and the program exits.

9. The current character is stored in `tmpc[0].`

10. The current character is concatenated with the existing input string using `strcat`.

11. The `while` loop continues until the terminating condition is met.

12. Once the input is complete, the memory allocated for the input string is freed using `free(input)`.

### **Usage**

1. The code prompts the user to enter any text.

2. The user can input text of any length.

3. The code dynamically allocates memory to store the input string, expanding the allocation as needed.

4. The input string is stored in the `input` variable for further processing and then freed afterwards.

5. After the input is processed, the allocated memory is freed using `free(input)` to avoid memory leaks.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define EXPANSION_FACTOR 1.5
```

```c
    ...
    fputs("Enter any text:\n", stdout);
    char tmpc[2] = "0\0";
    char *input = NULL;
    int strsize = 8; /* starting size */
    int tmp = EOF;

    if ((input =(char *)calloc(strsize, sizeof(char))) == NULL) {
        fputs("Cannot create input string.", stderr);
        exit(EXIT_FAILURE);
    }
    while (tmp) {
        tmp = fgetc(stdin);

        if (tmp == EOF || tmp == '\n')
            tmp = 0;

        if (strlen(input) == strsize-1) {
            strsize *= EXPANSION_FACTOR;
            if ((input = (char *)realloc(input, strsize)) == NULL) {
                fputs("Reallocation failed.", stderr);
                exit(EXIT_FAILURE);
            }
        }
        tmpc[0] = (char)tmp;
        strcat(input, tmpc);
    }
    ...
    free(input);
```

### Videogame-Style Text Output

This code template allows you to output text in a way that resembles the gradual display seen in certain videogames. Each character is printed with a small delay, creating an effect similar to in-game text dialogues.

### Code Explanation

1. The code uses a `for` loop to iterate over each character in the `text` string.
2. If the current character is a newline ('`\n`'), it pauses for one second using the `Sleep` function. This creates a line break effect in the output.
3. The character is then printed to the standard output using `fputc`.
4. The standard output is flushed using `fflush` to ensure the character is immediately displayed.
5. A short delay of 30 milliseconds is introduced using `Sleep` before proceeding to the next character.

This code template provides a simple and reusable way to create in-game text displays or other gradual text output effects in your programs.

### Usage

1. Replace the `"..."` in the `char *text` variable with the desired text you want to display.
2. Run the program.
3. The text will be output character by character, with a small delay between each character. Newlines ('`\n`') will introduce a pause of one second.

Note that it depends on `windows.h` and `stdio.h`.

```c
#include <windows.h>
#include <stdio.h>
```

```c
int main(void)
{
    char *text = "...";

    for (int i = 0; i < strlen(text); i++) {
        if (text[i] == '\n') {
            Sleep(1000);
        }
        if ((fputc((int)text[i], stdout)) == EOF)
            perror("fputc() failed");
        fflush(stdout);
        Sleep(30);
    }

    return EXIT_SUCCESS;
}
```

## Python

Heh, empty... for now :D
