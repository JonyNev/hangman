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
def print_pic(a):
    global pic
    pic=0
    if a==1:
        pic=picture1
    elif a==2:
        pic=picture2
    elif a==3:
        pic=picture3
    elif a==4:
        pic=picture4
    elif a==5:
        pic=picture5
    elif a==6:
        pic=picture6
    else:
        pic=picture7
print("""  _    _                                         
 | |  | |                                        
 | |__| | __ _ _ __   __ _ _ __ ___   __ _ _ __  
 |  __  |/ _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
 | |  | | (_| | | | | (_| | | | | | | (_| | | | |
 |_|  |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                      __/ |                      
                     |___/""")
String = ''
print("welcome to the hangman game \n \nplayer 1: ")
while (String == '') or (String.count(" ") == len(String)):
     String = str(input("choose words: "))
String = String.lower()
List_String = String.split(" ")

bord = ''
StringA = ''
answer = ''
answerp = answer

nub = 0
wrong=()
wrong= tuple(wrong)

for w in range(len(List_String)):
    StringA = StringA + List_String[w]
    num = len(List_String[w])
    print(num)
    Bord_bilude = '_  '
    bord = bord + Bord_bilude*num + "  "
    for i in range(1,num+1):
        nub = int(nub) + 1
        nub = str(nub)
        answer =  answer + ' ' + nub + ','
    answer = answer + "  "
print(answer,"\n\n\n\n\n\n\n\n\n\n\n\n\n\n player 2: \n  ",bord)

count = 0
while (answer.count(",")!=0) and count<7:
    gess = ''
    while(len(gess) != 1 or gess == ' '):  
        gess = str(input("gess a leter : " ))
        gess = gess.lower()         
        if answerp.count(gess)>0:
            print("\nyou got thise leter you don't need to try again")
            gess = ''
    if gess in String :
                  
        for i in range(String.count(gess)):
                 
            find0 = StringA.find(gess)+1
            find0 = ' ' + str(find0) + ","
            StringA = StringA.replace(gess,' ',1)
            gess0 = gess + "  "
                          
            if find0==' 1,':
                gess0=gess0.capitalize()
                         
            answer = answer.replace(find0,gess0)
            answerp = answer
                        
            for i in range(1,len(StringA)+1):
                nub = i
                nub = ' ' + str(nub) + ','
                answerp = answerp.replace(nub,"   ")
                  
        print("\n\n\n\n  ",answerp,"\n  ",bord)

    else:
        if gess in wrong:
            print ("\ntry harder!\n",wrong)  
        else:
            gess = tuple(gess)
            wrong = wrong + gess
            count = count + 1
            print_pic(count)
            print ("\n\n\nwrong answer:\n",pic,wrong)  

if (answer.count(",")==0):
    print ("well done \n numbers of wrong answer:",count)   

else:
    print ("game over:\n    _\n   | |\n   O |\n  -|-|\n  / \|\n   __|__")
