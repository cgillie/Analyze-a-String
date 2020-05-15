# Analyze-a-String
Analyze a user entered string.
#include <iostream>
#include<cctype>
using namespace std;

int countVowels(char *, int); // Function prototype
int countLetters(char *, int);
int countNumbers(char *, int);

int main ()
{
const int SIZE = 51;
char userString[SIZE];

cout << "\nEnter a string (up to 50 characters): ";
cin.getline(userString, SIZE); 

//**************************
// Constants for menu choices
const int COUNT_VOWELS = 1,
COUNT_CONS = 2,
COUNT_NUM = 3,
COUNT_LETTERS = 4,
ENTER_NEW_LINE = 5,
QUIT_CHOICE = 6;
// Variables
int choice;

do
{
//Display the menu.
cout << "\n\tSearching and Counting Characters from a String Using Pointers Menu\n\n" 
<< "1. Count Vowels\n"
<< "2. Count Consonants\n"
<< "3. Count Numbers\n"
<< "4. Count Letters\n"
<< "5. Enter New Line\n"
<< "6. Quit Program\n\n"
<< "Enter your choice: "; cin >> choice;
// Validate the menu selection.
while (choice < COUNT_VOWELS || choice > QUIT_CHOICE)
{
cout << "Please enter a valid menu choice: ";
cin >> choice;
}

switch (choice)
{
  //Menu item 1
  case COUNT_VOWELS:
  cout << "There are " << countVowels(userString, SIZE) << " vowels.\n"; break;
  //Menu item 2
  case COUNT_CONS:
  cout << "There are " << countLetters(userString, SIZE)-countVowels(userString, SIZE) << " consonants.\n"; break;
  //Menu item 3
  case COUNT_NUM:
  cout << "There are " << countNumbers(userString, SIZE) << " numbers.\n"; break;
 //Menu item 4
  case COUNT_LETTERS:
  cout << "There are " << countLetters(userString, SIZE) << " letters.\n"; break;
  //Menu item 5
  case ENTER_NEW_LINE:
  cout << "\n*****************************************\n\nEnter a string (up to 50 characters): ";
  cin >> userString;
  break;
}

cout << "End of iteration\n\n";
} while (choice != QUIT_CHOICE);

cout << "End of program";
return 0;
}
//End of Main Function *****************************************

//Function Count Vowels ****************************************
int countVowels(char *strPtr, int SIZE)
{
int vowels = 0;

// Step through the string counting vowels
while (*strPtr != '\0')
{
if (*strPtr == 'a' || *strPtr == 'e' || *strPtr =='i' || *strPtr =='o' || *strPtr =='u' || *strPtr =='A' || *strPtr =='E' || *strPtr =='I' || *strPtr =='O' || *strPtr =='U') 
  vowels++;

strPtr++;
}
return vowels;
}


//Function Count Consonants **************************************
int countLetters(char *strPtr, int SIZE)
{
int letters = 0; // Number of letters

// Step through the string counting letters
while (*strPtr != '\0')
{
  if (isalpha(*strPtr))
  letters++;
  
  strPtr++;
}
return letters;
}

//Function Count Numbers **************************************
int countNumbers(char *strPtr, int SIZE)
{
int numbers = 0; // Number of letters

// Step through the string counting letters
while (*strPtr != '\0')
{
  if (isdigit(*strPtr))
  numbers++;
  
  strPtr++;
}
return numbers;
}
