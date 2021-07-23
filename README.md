# TIC-TAC-TOE
# a simple GUI tic-tac-toe python project which tries maximum to win or make a tie
from tkinter import *
import random
b=[[0,0,0],[0,0,0],[0,0,0]]
def next_turn(row, column):
    
    #print(b)
    flag=1
    c0,c1,c2,r0,r1,r2,d1,d2=0,0,0,0,0,0,0,0
    player=['X','O']
    if(flag==1):
        done=0
        x=row
        y=column
        #print(b[x][y])
        if(b[x][y]==1 or b[x][y]==-1):
            print('wrong input')
        else:
            #print('b=',b)
            a[x][y]['text']=player[0]
            b[x][y]=-1
            c0=b[0][0]+b[1][0]+b[2][0]
            c1=b[0][1]+b[1][1]+b[2][1]
            c2=b[0][2]+b[1][2]+b[2][2]
            r0=b[0][0]+b[0][1]+b[0][2]
            r1=b[1][0]+b[1][1]+b[1][2]
            r2=b[2][0]+b[2][1]+b[2][2]
            d1=b[0][0]+b[1][1]+b[2][2]
            d2=b[0][2]+b[1][1]+b[2][0]
            check=[d1,d2,r0,r1,r2,c0,c1,c2]
            maximum=max(check)
            minimum=min(check)
            if(maximum==3):
                print('you lost')
                flag=0
            if(minimum==-3):
                print("you won")
                flag=0
            low=check.index(minimum)
            #fill diagonal d1
            if(low==0):
                for j in range(3):
                    if(b[j][j]!=-1 and b[j][j]!=1):
                        b[j][j]=1
                        a[j][j]['text']=player[1]
                    
                        done=1
                        break
            #fill r0
            elif(low==2):
                for j in range(3):
                    if(b[0][j]!=-1 and b[0][j]!=1):
                        b[0][j]=1
                        #print('entered')
                        #print(b)
                        a[0][j]['text']=player[1]
                        
                        done=1
                        break
            #fill r1
            elif(low==3):
                for j in range(3):
                    if(b[1][j]!=-1 and b[1][j]!=1):
                        b[1][j]=1 
                        a[1][j]['text']=player[1]
                        
                        done=1
                        break
            #fill r2
            elif(low==4):
                for j in range(3):
                    if(b[2][j]!=-1 and b[2][j]!=1):
                        b[2][j]=1 
                        a[2][j]['text']=player[1]
                        
                        done=1
                        break
            #fill h0
            elif(low==5):
                for j in range(3):
                    if(b[j][0]!=-1 and b[j][0]!=1):
                        b[j][0]=1 
                        a[j][0]['text']=player[1]
                        
                        done=1
                        break
            #fill h1
            elif(low==6):
                for j in range(3):
                    if(b[j][1]!=-1 and b[j][1]!=1):
                        b[j][1]=1 
                        a[j][1]['text']=player[1]
                        
                        done=1
                        break
            #fill h2
            elif(low==7):
                for j in range(3):
                    if(b[j][2]!=-1 and b[j][2]!=1):
                        b[j][2]=1 
                        a[j][2]['text']=player[1]
                        
                        done=1
                        break
            #fill d2
            else:
                if(b[2][0]==-1 and b[1][1]==-1):
                    b[0][2]=1
                    a[0][2]['text']=player[1]
                    
                    done=1
                    #break
                if(b[0][2]==-1 and b[1][1]==-1):
                    b[2][0]=1
                    a[2][0]['text']=player[1]
                
                    done=1
                    #break
                if(b[0][2]==-1 and b[2][0]==-1):
                    b[0][2]=1
                    a[0][2]['text']=player[1]
                    done=1
                    #break
            if(done!=1):
                for j in range(3):
                    for k in range(3):
                        if(b[j][k]==0):
                            b[j][k]=1 
                            a[j][k]['text']=player[1]
                            
                            done=1
                            break
                    if(done==1):
                        break
            if(done!=1):
                print('finished')
                flag=0
    
window = Tk()
window.title("Tic-Tac-Toe")
a = [[0,0,0],
           [0,0,0],
           [0,0,0]]

frame = Frame(window)
frame.pack()

for row in range(3):
    for column in range(3):
        a[row][column] = Button(frame, text="",font=('consolas',40), width=5, height=2,
                                      command= lambda row=row, column=column: next_turn(row,column))
        a[row][column].grid(row=row,column=column)

window.mainloop()
