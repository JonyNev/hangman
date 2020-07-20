# hangman

picture1= ("x-------x")

picture2=("""    x
     |
     |
     |
     |
     | 
 x---x---x """)

picture3 = ("""     x----x
      |
      |
      |
      |
      | 
 x----x-----x """)
picture4 = ("""     x----x
      |    |
      |    
      |    
      |    
      | 
 x----x-----x """)
picture5 = ("""     x----x
      |    |
      |    O
      |    
      |    
      | 
 x----x-----x """)

picture6 = ("""     x----x
      |    |
      |    O
      |   -|-
      |    
      | 
 x----x-----x """)
picture7 = ("""     x----x
      |    |   
      |    O   
      |   -|-  
      |   / \  
      | 
 x----x-----x   """)
def What_To_Print(a):
    global loss
    loss=0
    if a==1:
        loss=picture1
    elif a==2:
        loss=picture2
    elif a==3:
        loss=picture3
    elif a==4:
        loss=picture4
    elif a==5:
        loss=picture5
    elif a==6:
        loss=picture6
    else:
        loss=picture7
print("""  _    _                                         
 | |  | |                                        
 | |__| | __ _ _ __   __ _ _ __ ___   __ _ _ __  
 |  __  |/ _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
 | |  | | (_| | | | | (_| | | | | | | (_| | | | |
 |_|  |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                      __/ |                      
                     |___/""")
print("welcome to the hangman game \n \nplayer 1: ")
CHOSEN_WORDS = ''
while (CHOSEN_WORDS == '') or (CHOSEN_WORDS.count(" ") == len(CHOSEN_WORDS)):
     CHOSEN_WORDS = str(input("choose words: "))
CHOSEN_WORDS = CHOSEN_WORDS.lower()

String_chars = ''
List_words = CHOSEN_WORDS.split(" ")


String_position_for_chars = ''
String_num_build = 0

progras_untill_now = String_position_for_chars

chars_used=()
chars_used= tuple(chars_used)

BORD = ''
Bord_build = '_  '

gess_a_leter = ''
    
for w in range(len(List_words)):
    String_chars = String_chars + List_words[w]
    lengh_of_word_x = len(List_words[w])
    BORD = BORD + Bord_build*lengh_of_word_x + "  "
    
    for i in range(1,lengh_of_word_x+1):
        String_num_build = int(String_num_build) + 1
        String_num_build = str(String_num_build)
        String_position_for_chars =  String_position_for_chars + ' ' + String_num_build + ','
    
    String_position_for_chars = String_position_for_chars + "  "

print("-----------------------------------\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n player 2: \n  ",BORD)
numbers_of_losses = 0

while (String_position_for_chars.count(",")!=0) and numbers_of_losses<7:
    gess_a_leter = ''              
    while(len(gess_a_leter) != 1 or gess_a_leter == ' '):  
        gess_a_leter = str(input("gess a leter : " ))
        gess_a_leter = gess_a_leter.lower()         
        
        if progras_untill_now.count(gess_a_leter)>0:
            print("-----------------------------\nyou got this leter you don't need to try again")
            gess_a_leter = ''
    
    if gess_a_leter in CHOSEN_WORDS :
                  
        for i in range(CHOSEN_WORDS.count(gess_a_leter)):
                 
            position_in_chosen_word = String_chars.find(gess_a_leter)+1
            position_in_chosen_word = ' ' + str(position_in_chosen_word) + ","
            String_chars = String_chars.replace(gess_a_leter,' ',1)
            replace_num_in_answer = gess_a_leter + "  "
            if position_in_chosen_word ==' 1,':
                replace_num_in_answer=replace_num_in_answer.capitalize()
                         
            String_position_for_chars = String_position_for_chars.replace(position_in_chosen_word,replace_num_in_answer)
            progras_untill_now = String_position_for_chars
                        
            for i in range(1,len(String_chars)+1):
                String_num_build = i
                String_num_build = ' ' + str(String_num_build) + ','
                progras_untill_now = progras_untill_now.replace(String_num_build,"   ")
                  
        print("-------------------\n\n\n  ",progras_untill_now,"\n  ",BORD,"\n  ",chars_used)
    else:
        if gess_a_leter in chars_used:
            print ("--------------------\ntry harder!\n",chars_used,"\n  ",progras_untill_now,"\n  ",BORD)  
        else:
            gess_a_leter = tuple(gess_a_leter)
            chars_used = chars_used + gess_a_leter 
            numbers_of_losses = numbers_of_losses + 1
            What_To_Print(numbers_of_losses)
            print ("---------------------\n\n\nwrong answer:\n",loss,chars_used,"\n  ",progras_untill_now,"\n  ",BORD)  
if (String_position_for_chars.count(",")==0):
    print ("well done \n numbers of wrong answer:",numbers_of_losses)   
else:
    print ("""      
    _       _____    
   | |    /  ___  \   __ _  _ __ ___  __ _      ___  _    _  __ _   _ __                                         
   O |   /  /  _\__  / _` | '_ ` _ \ / X _)    / _ \ \ \/ / / X _) | '_ ;                                  
  -|-|   \  \ |_  \   (_| | | | | | |  /_       (_) | \  / |   /_  | |                                  
  / \|    \  \__/    \__,_|_| |_| |_|\__ _)    \___/   \/   \__ _) |_|                         
   __|__   \______/                                                                  """)

