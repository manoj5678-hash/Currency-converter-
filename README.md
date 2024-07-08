# Currency-converter-
import tkinter as tk
from tkinter import *
from tkinter import ttk
from datetime import datetime
import requests
from PIL import imageTk, image
from tkinter import messagebox

root=tk.Tk()
root.geometry("700*270")
root.title("Currency Converter")
root.iconbitmap('icon.ico')
root.maxsize(600,270)
root.minsize(600,270)

image=image.open('currency.png')
zoom=0.5

pixels_x,pixels_y=tuple([int(zoom*x) for x in image size])

img=imageTk.photoimage(image.resize((pixels_x,pixels_y)))
panel=label(root,image=img)
panel.place(x=190,y=35)

def show_data():
    amount=E1.get()
    from_currency=c1.get()
    to_currency=c2.get()
    url='http://api.currencylayer.com/live?access_key=4273d2c37f738367f08780b934ce7dda&format=1'
    if amount=='':
       messagebox.showerror("currency converter","please fill the amount")
    elif to_currency =='':
       messagebox.showerror("currency converter ", please choose the currency")

else:
       data= requests.get(url).json()
       currency=from_currency.strip()+to_currency.strip()
       amount=int(amount)
       cc=data['quotes'][currency]
       cur_conv=cc*amount 
       E2.insert(0,cur_conv)

       text.insert('end',f'{amount} united state dollar equals{cur_conv}{to_currency}\n\n last time update---\t{datetime.now()}')

def clear():
         E1.delete(0,'end')
         E2.delete(0,'end')
         text.delete(1.0,'end')

l1=label(root,text="USD currency converter using python",font=('verdana','10','bold'))
l1.place(x=150,y=15)

amt=label(root,text="amount",font=('roboto',10,'bold'))
amt.place(x=20,y=15)
E1=entry (root,width=20,borderwidth=1, font=('roboto',10,'bold'))
E1.place(x=20,y=40)

c1=tk.stringvar()
c2=tk.stringvar()
currencychoose1=ttk.combobox(root,width=20,textvariable=c1,state='readonly',font=('verdana',10,'bold'))

currencychoose1['values']=('USD',)
currencychoose1.place(x=300,y=40)
currencychoose1.current(0)

E2=entry(root,width=20,borderwidth=1,font=('roboto',10,'bold'))
E2.place(x=20,y=80)

currencychoose2 = ttk.combox(root,width=20,textvariable=c2,
