# RoulettePython
A simple roulette game in pyhton with only graphics.py library.
 The language is in Italian, i'll update it in English too soon.

#Inizio
from graphics import *
from math import *

def main():

    #Pagina Iniziale
    
    win = GraphWin("Roulette", 500, 500)
    win.setBackground("green")
    
    pt1 = Point(40,220)
    pt2 = Point(460,220)
    Lne = Line(pt1,pt2)
    Lne.setOutline(color_rgb(250,250,250))
    Lne.draw(win)

    txt = Text(Point(250,200), "Benvenuto al gioco della Roulette!")
    txt.setSize(20)
    txt.setTextColor(color_rgb(250, 250 ,250))
    txt.draw(win)

    Rec = Rectangle(Point(170,260),Point(330,300))
    Rec.draw(win)
    Rec.setOutline(color_rgb(250,250,250))

    txt2 = Text(Point(250,280),"Gioca")
    txt2.setOutline(color_rgb(250,250,250))
    txt2.setSize(18)
    txt2.draw(win)

    win.getMouse()
    win.close()

    #Budget

    Budget = int(1000)
    #Pagina 2

    Count = 0

    win2 = GraphWin("Roulette",700,700)
    win2.setBackground("green")

    

     ##Immagine Roulette

    img = Image(Point(350, 350), "roul.png")
    img.draw(win2)

    ok = Rectangle(Point(455,585),Point(485,615))
    ok.setOutline("White")
    ok.draw(win2)

    ok2 = Text(Point(470,600),"OK")
    ok2.setSize(12)
    ok2.setOutline("White")
    ok2.draw(win2)

    while Count < 100:

    ##Testo "Quanto vuoi puntare?"

        txt2 = Text(Point(350,570),"Quanto vuoi puntare?")
        txt2.setSize(17)
        txt2.setTextColor("White")
        txt2.draw(win2)

    ##Box Puntata
    
        box = Entry(Point(350,600),20)
        box.setText(0)
        box.draw(win2)

    ##Testo "Budget"

        b1txt = Text(Point(52,20),"Budget:")
        b1txt.setSize(18)
        b1txt.setOutline("White")
        b1txt.draw(win2)
    
        btxt = Text(Point(117,20),(Budget))
        btxt.setSize(18)
        btxt.setOutline("White")
        btxt.draw(win2)

        #Puntata

        Giri = 1

        while Giri > 0:

            win2.getMouse()
        
            Puntata= int(box.getText())

            if Puntata <= Budget:
                Giri = Giri - 1
                if Puntata <= 0:
                    txt2.setText("Non puoi puntare meno di Zero!")
                    Giri = 1
            else:
                txt2.setText("Non hai abbastanza soldi per puntare cosÃ¬ alto!")
                Giri = 1

        Puntata = box.getText()

        win2.getMouse()
               
            
        #Puntata Testo

        ptxt = Text(Point(350,630),"Hai Puntato:")
        ptxt.setSize(15)
        ptxt.setOutline("White")
        ptxt.draw(win2)

        ptxt = Text(Point(350,655),(Puntata))
        ptxt.setSize(15)
        ptxt.setOutline("White")
        ptxt.draw(win2)

        #ModalitÃ 

        box.setText("")

        txt2.setText("Su quali numeri vuoi puntare? Pari o Dispari?")
        txt2.setSize(13)

        pd = 1

        while pd > 0:

            win2.getMouse()

            Modalita = box.getText()

            if not Modalita == "Pari" or "Dispari":
                pd = 0
            else:
                txt2.setText("Scrivi Pari o Dispari!")
                pd = 1
                

        if Modalita == "Pari":
            Modalita = int(1)
        else:
            Modalita= int(2)

        #Roulette

        oktxt = Text(Point(350,680),"Clicca per girare la Roulette!")
        oktxt.setSize(10)
        oktxt.setOutline("Black")
        oktxt.draw(win2)

        win2.getMouse()
        oktxt.move(1000,1000)

        import random
        for x in range(1):
            Numero = random.randint(0,37)

        numtxt= Text(Point(350,80),Numero)
        numtxt.setSize(20)
        numtxt.setOutline("White")
        numtxt.draw(win2)

        #Guadagno

        guadtxt= Text(Point(550,20),"")
        guadtxt.setSize(18)
        guadtxt.setOutline("White")
        guadtxt.draw(win2)
        guad2txt= Text(Point(650,20),"")
        guad2txt.setSize(18)
        guad2txt.setOutline("White")
        guad2txt.setStyle("bold")
        guad2txt.draw(win2)
        
        win2.getMouse()

        Vincita = int(Budget) + int(Puntata) + int(Puntata)

        Vincita2 = int(Puntata) + int(Puntata)

        Perdita2 = int(Puntata)

        Perdita = int(Budget) - int(Puntata)

        Resto = Numero%2

        for x in range(2):
        
            if Resto > 0:
                if Modalita > 1:
                    Budget = Vincita
                    numtxt.setText("Hai Vinto!")
                    win2.getMouse()
                    guadtxt.setText("Hai Vinto:")
                    guad2txt.setText(Vincita2)
                else:
                    Budget = Perdita
                    numtxt.setText("Hai Perso!")
                    win2.getMouse()
                    guadtxt.setText("Hai Perso:")
                    guad2txt.setText(Perdita2)
            else:
                if Modalita < 2:
                    Budget = Vincita
                    numtxt.setText("Hai Vinto!")
                    win2.getMouse()
                    guadtxt.setText("Hai Vinto:")
                    guad2txt.setText(Vincita2)
                else:
                    Budget = Perdita
                    numtxt.setText("Hai Perso!")
                    win2.getMouse()
                    guadtxt.setText("Hai Perso:")
                    guad2txt.setText(Perdita2)

        guadtxt.setText("")
        guad2txt.setText("")
        btxt.setText("")
        txt2.setText("")
        ptxt.setText("")
        numtxt.setText("")
            
        
main()
#--------------------------------------------------------------------------




















