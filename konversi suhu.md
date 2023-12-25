from tkinter import *
import tkinter.font

root =Tk()
root.title("tempconverter")
root.geometry("400x400")

thefont = tkinter.font.Font(size=15)

nwframe = LabelFrame(root,text="remp converter",padx=150,pady=150)
nwframe.place(x =13, y = 15)

judul = Label(nwframe, text="temperature").grid(row = 0, column=3)
samde = Label(nwframe, text="=").grid(row = 1,column=1)

e1 = Entry(nwframe, width=20)
e2 = Entry(nwframe, width=20)
e1["font"] = thefont
e2["font"] = thefont
e2.insert(0, "0")
e1.grid(row=1,column=0)
e2.grid(row=1, column=2)

rmslbl = Label(nwframe,text="Formula",bg="yellow")
rmslbl.place(x = 1,y =90)

rmsnya = Label(nwframe,text="(...°c x 9/5) + 32 =...°F")
rmsnya.place(x =50, y = 90)

chek = {"rumus","yes"}

def rumus(rm):
 
    e2.delete(0,END)
    kotaksatu = cliked.get()
    kotakdua = cliked2.get()
    nomor1 = int(e1.get())

    global rmsnya
    if "rumus" in chek:
        rmsnya.place_forget()
    else:
        pass
    if kotaksatu == "celcius" and kotakdua == "fahrentheit":
        rmsnya = Label(nwframe, text="("+e1.get()+"°C x 9/5)+32=...°F")
        hitungan = (nomor1 * 9/5) + 32    
    elif kotaksatu == "celcius" and kotakdua == "kelvin":
        rmsnya = Label(nwframe, text=e1.get()+"°C + 273.15 =... K")
        hitungan = (nomor1 +273.15)    
    elif kotaksatu == "celcius" and kotakdua == "reamur":
        rmsnya = Label(nwframe,text="(4/5 x "+e1.get()+"°C)=...R")
        hitungan = (4/5 * nomor1)    
    elif kotaksatu == "fahrentheit" and kotakdua == "celcius":
        rmsnya = Label(nwframe, text="("+e1.get()+"°F-32)x5/9=...°C")
        hitungan = (nomor1 - 32) * 5/9    
    elif kotaksatu == "fahrentheit" and kotakdua == "kelvin":
        rmsnya = Label(nwframe, text="("+e1.get()+"F-32)X5/9+273.15=...K")
        hitungan = (nomor1 - 32) * 5/9 + 273.15    
    elif kotaksatu == "fahrentheit" and kotakdua == "reamur":
        rmsnya = Label(nwframe, text="("+e1.get()+"F-32)x4/9=...R")
        hitungan = (nomor1 -32) * 4/9    
    elif kotaksatu == "reamur" and kotakdua == "celcius":
        rmsnya = Label(nwframe, text="(5/4x"+e1.get()+"R)=...°C")
        hitungan = (5/4 * nomor1)    
    elif kotaksatu == "reamur" and kotakdua == "fahrentheit":
        rmsnya = Label(nwframe, text="(9/4X"+e1.get()+"R)+32=...F")
        hitungan = (9/4 * nomor1) * 32    
    elif kotaksatu == "reamur" and kotakdua == "kelvin":
        rmsnya = Label(nwframe, text="(5/4x"+e1.get()+"R)+273=...K")
        hitungan = (5/4 * nomor1) +2    
    elif kotaksatu == "kelvin" and kotakdua == "celcius":
        rmsnya = Label(nwframe, text=e1.get()+"K-273.15=...°C")
        hitungan = (nomor1 - 273.15)    
    elif kotaksatu == "kelvin" and kotakdua == "fahrentheit":
        rmsnya = Label(nwframe, text="("+e1.get()+"K-273.15)x9/5+32=...°F")
        hitungan = (nomor1 - 273.15) * 9/5 + 32    
    elif kotaksatu == "kelvin" and kotakdua == "reamur":
        rmsnya = Label(nwframe, text="("+e1.get()+"K-273)x4/5=...R")
        hitungan = (nomor1 - 273) * 4/5    
    elif kotaksatu == "celcius" and kotakdua == "celcius" or kotaksatu == "fahrentheit" and kotakdua == "fahrentheit" or "reamur" and kotakdua == "reamur" or kotaksatu == "kelvin" and kotakdua == "kelvin" :
       
        rmsnya = Label(nwframe, text="tidak ada rumus")
        hitungan = nomor1
    hasil = hitungan
    e2.insert(0,hasil)
    rmsnya.place (x = 50, y = 90)   


option = ["celcius","fahrentheit","kelvin","reamur"]
cliked = StringVar()
cliked.set(option[0])
drop = OptionMenu(nwframe,cliked,*option,command=rumus)
drop.config(width=20)
drop.grid(row = 2,column=0)

cliked2 = StringVar()
cliked2.set(option[0])
drop2 = OptionMenu(nwframe,cliked2,*option,command=rumus)
drop2.config(width=20)
drop2.grid(row = 2,column=2)

btn = Button(nwframe,text="count", command=lambda:rumus("hitung"))
btn.grid(row=25,column=2)



root.mainloop()
