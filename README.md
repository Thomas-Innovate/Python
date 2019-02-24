#9_lives

import random

lives = 9

words = ['plane','pizza','fairy','otter','shirt','grand','sleepy','smelly','brave','beautiful','cheesy','blue','fat','thin','fresh','bright','gloomy','perfect','great','awesome','soft','hard','gray','curly','flat','neat','proud','fluffy','pink','juicy','obvious','strong','lazy','hot','cold','rigid','frozen','smooth','apple','ball','cat','giraffe','cheese','pillow','duck','dragon','fire','blanket','television','picture','bar','zebra','battleship','spaceship','password','design','book','worm','hamster','table','sofa','pot','wall','laptop','computer','tiger','towel','tower','sock','tree','shirt','jacket','sweater','pants','shoes','mammoth','food','bed','whale']

print('\n9 lives\n')
secret_word = random.choice(words)
clue = []
index = 0
while index < len(secret_word):
  clue.append('?')
  index += 1

heart_symbol = u'\u2764'
guessed_word_correctly = False

unknown_letters = len(secret_word)

def update_clue(guessed_letter, secret_word, clue, unknown_letters):
  index = 0
  while index < len(secret_word):
    if guessed_letter == secret_word[index]:
      clue[index] = guessed_letter
      unknown_letters -= 1
    index += 1

  return unknown_letters

while lives > 0:
  print(clue)
  print('Lives left: ' + heart_symbol * lives + ' (' + str(lives) + ') ')
  guess = input('Guess a letter or the whole word: ')

  if guess == secret_word:
    guessed_word_correctly = True
    break

  if guess in secret_word:
    unknown_letters = update_clue(guess, secret_word, clue, unknown_letters)
  else:
    print('Incorrect, you lose a life.')
    lives -= 1

  if unknown_letters == 0:
    guessed_word_correctly = True
    break



if guessed_word_correctly == True:
  print('You won! The secret word was ' + secret_word)
else:
  print('You lost! The secret word was ' + secret_word)

#Signature
print('\n9 lives created by Thomas\nMade on 2/20/2019')
print('\nProgram Ended')
