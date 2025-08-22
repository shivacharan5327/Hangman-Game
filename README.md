# Hangman-Game 
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>
#define MAX_TRIES 6
// Function to display the hangman figure based on wrong guesses
void draw_hangman(int wrong)
 {   
          printf("\n +---+\n"); 
            printf(" |   %c\n", (wrong >= 1) ? 'O' : ' ');    
       printf(" |  %c%c%c\n", (wrong >= 3) ? '/' : ' ', (wrong >= 2) ? '|' : ' ', (wrong >= 4) ? '\\' : ' ');   
       printf(" |  %c %c\n", (wrong >= 5) ? '/' : ' ', (wrong >= 6) ? '\\' : ' ‘);  
           printf(" |\n");   
        printf("=========\n");}
int main() 
{    
        char word[100], guessed[100];    
        char display[100];  
          int wrong = 0, len, correct = 0, i;    
           char guess;        // Sample secret word   
          strcpy(word, "hangman");    
             len = strlen(word);        // Initialize display with underscores                               for (i = 0; i < len; i++) 
       {        display[i] = '_';    }    
            display[len] = '\0';   
          printf("🎮 Welcome to Hangman Game in C 🎮\n");   
            while (wrong < MAX_TRIES && correct < len) 
               {        draw_hangman(wrong);     
                           printf("Word: ");    
                          for (i = 0; i < len; i++) 
                      {            printf("%c ", display[i]);        }  
                                     printf("\n");       
                                 printf("Guess a letter: ");        
                              scanf(" %c", &guess);    
                         guess = tolower(guess);   
                             int found = 0;     
                         for (i = 0; i < len; i++) 
                         {          
                                if (word[i] == guess && display[i] == '_’)
                                {             
                                             display[i] = guess;        
                                                    correct++;              
                                              found = 1;            
                                   }     
                           }       
                                        if (!found)
                                   {            wrong++;   
                                            printf("Wrong guess! 😢\n");    
                                   } else
                                           {            printf("Correct! 😊\n");     
                                           } 
                                 }  
                                         draw_hangman(wrong);   
                                         if (correct == len)
                         {        printf("🎉 Congratulations! You guessed the word: %s\n", word);   
                        } else
                      {  
                      printf("💀 Game Over! The correct word was: %s\n", word); 
                      } 
           return 0;
               }
