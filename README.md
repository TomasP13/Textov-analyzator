# Textový-analyzator
'''
projekt_1.py: První projekt do Engeto Online Python Akademie
============================================================
autor: Tomáš Paluzga
email: tomas.paluzga@gmail.com
discord: Tomas P.#5811

'''
TEXTS =['''
Situated about 10 miles west of Kemmerer,
Fossil Butte is a ruggedly impressive
topographic feature that rises sharply
some 1000 feet above Twin Creek Valley
to an elevation of more than 7500 feet
above sea level. The butte is located just
north of US 30N and the Union Pacific Railroad,
which traverse the valley. ''',
'''At the base of Fossil Butte are the bright
red, purple, yellow and gray beds of the Wasatch
Formation. Eroded portions of these horizontal
beds slope gradually upward from the valley floor
and steepen abruptly. Overlying them and extending
to the top of the butte are the much steeper
buff-to-white beds of the Green River Formation,
which are about 300 feet thick.''',
'''The monument contains 8198 acres and protects
a portion of the largest deposit of freshwater fish
fossils in the world. The richest fossil fish deposits
are found in multiple limestone layers, which lie some
100 feet below the top of the butte. The fossils
represent several varieties of perch, as well as
other freshwater genera and herring similar to those
in modern oceans. Other fish such as paddlefish,
garpike and stingray are also present.'''
]



#Registrovaní uživatelé
#+------+-------------+
#| user |   password  |
#+------+-------------+
#| Bob  |     123     |
#| Ann  |   pass123   |
#| Mike | password123 |
#| Liz  |   pass123   |
#+------+-------------+

#Přihlašovací údaje
uzivatele = {
    "Bob": "123",
    "Ann": "pass123", 
    "Mike": "password123", 
    "Liz": "pass123"
}

oddelovac = (50* "-")
oddelovac_1 = (50* "=")

uzivatel = input("Zadej jmeno:  ")

if uzivatel in uzivatele:
    heslo = input("Zadej heslo:  ")
    print(oddelovac)
    if uzivatele.get(uzivatel) == heslo:
        print(f"Vítej {uzivatel},zadej číslo textu a pokračuj v analýze" )
        print(oddelovac)
    else:
        print("Špatné heslo!")
        print('Ukončuji!')
        quit()
else:
    print("Neregistrovaný uživatel!")
    print('Ukončuji!')
    quit()

#Výběr textu

text = input("Zadej číslo textu v rozmezí 1-3:  ")
print(oddelovac)

texty = {"1":TEXTS[0], "2": TEXTS[1], "3": TEXTS[2] }


if text in texty:
    print("Pokračuj s textem č.:",''.join(text), "v analýze")
    print(oddelovac_1)
else:
    print("Zadaný text neexistuje!")
    print("Ukončuji!")
    quit()

#Analýza textu 1
#----------------------------------------
#Počet slov:
text1 = TEXTS[0].split()
if "1" in text:
    vysledek1 = len(text1)
    print(f"text č.:{text} má {vysledek1} slov")

#Počet slov začínajíci velkým písmenem:
    VelP_slova = sum(map(str.istitle,text1))
    print(f'text č.:{text} má: {VelP_slova} slov',
    'začinájících velkým písmenem')
#Počet slov psaných velkými písmeny:
    slova_s_VelP = sum(map(str.isupper,text1))
    print(f'text č.:{text} má: {slova_s_VelP} slov',
    'psaná velkými písmeny')
#Počet slov psaných malými písmeny:
    slova_s_MalP = sum(map(str.islower,text1))
    print(f'text č.:{text} má: {slova_s_MalP} slov',
    's malými písmeny')
#Počet čísel:
    cisla = sum(map(str.isdigit,text1))
    print(f'text č.:{text} má: {cisla} čísel')
#Součet čísel:
    cisla1 = []
    soucet = 0
    for cis in text1:
        if cis.isdigit():
            cisla1.append(cis)
    for cis1 in cisla1:
        soucet += int(cis1)
    print(f'součet čísel v textu č.:{text} je: {soucet}\n')
    print(oddelovac_1)

#####
#délky slov vtextu 1:
    cisty_text = []
    rozdeleny_text = text1
    for slovo in rozdeleny_text:
        cisty_text.append(slovo.strip('0123456789').lower())
#délka slov
    delka_slov = []
    for slovo in cisty_text:
        delka_slov.append(len(slovo))
######
    pocet = dict()
    for slovo in delka_slov:
        if slovo not in  pocet:
            pocet[slovo] = 1
        else:
            pocet[slovo] = pocet[slovo] + 1
    del pocet[0]
#seřazení
    serazeny_vysledek = sorted(pocet.keys())
    vysledky = []
    for vyskyt in pocet:
        vysledky.append((pocet[vyskyt],vyskyt))
    print(f'Počet písmen slova   |  četnost slov  ')
    print(oddelovac)
    serazeny_vysledek = sorted(vysledky,reverse = True)
    for index, tupl in enumerate(serazeny_vysledek):            
        print(f" {tupl[1]}         {tupl[0]*'*'}     {tupl[0]}x")


#Analýza textu 2
#----------------------------------------
#Počet slov:

text2 = TEXTS[1].split()
if "2" in text:
    vysledek2 = len(text2)
    print(f"text č.:{text} má {vysledek2} slov")

#Počet slov začínajíci velkým písmenem:
    VelP_slova = sum(map(str.istitle,text2))
    print(f'text č.:{text} má: {VelP_slova} slov',
    'začinájících velkým písmenem')
#Počet slov psaných velkými písmeny:
    slova_s_VelP = sum(map(str.isupper,text2))
    print(f'text č.:{text} má: {slova_s_VelP} slov',
    'psaná velkými písmeny')
#Počet slov psaných malými písmeny:
    slova_s_MalP = sum(map(str.islower,text2))
    print(f'text č.:{text} má: {slova_s_MalP} slov',
    's malými písmeny')
#Počet čísel:
    cisla = sum(map(str.isdigit,text2))
    print(f'text č.:{text} má: {cisla} čísel')
#Součet čísel:
    cisla1 = []
    soucet = 0
    for cis in text2:
        if cis.isdigit():
            cisla1.append(cis)
    for cis1 in cisla1:
        soucet += int(cis1)
    print(f'součet čísel v textu č.:{text} je: {soucet}\n')
    print(oddelovac_1)

#####
#délky slov vtextu 2:
    cisty_text = []
    rozdeleny_text = text2
    for slovo in rozdeleny_text:
        cisty_text.append(slovo.strip('0123456789').lower())
#délka slov
    delka_slov = []
    for slovo in cisty_text:
        delka_slov.append(len(slovo))
######
    pocet = dict()
    for slovo in delka_slov:
        if slovo not in  pocet:
            pocet[slovo] = 1
        else:
            pocet[slovo] = pocet[slovo] + 1
    del pocet[0]
#seřazení
    serazeny_vysledek = sorted(pocet.keys())
    vysledky = []
    for vyskyt in pocet:
        vysledky.append((pocet[vyskyt],vyskyt))
    print(f'Počet písmen slova  |   četnost slov  ')
    print(oddelovac)
    serazeny_vysledek = sorted(vysledky,reverse = True)
    for index, tupl in enumerate(serazeny_vysledek):
        print(f" {tupl[1]}         {tupl[0]*'*'}     {tupl[0]}x")


#Analýza textu 3
#---------------------------------------------
#Počet slov:
text3 = TEXTS[2].split()
if "3" in text:
    vysledek3 = len(text3)
    print(f"text č.:{text} má: {vysledek3} slov")

#Počet slov začínajíci velkým písmenem:
    VelP_slova = sum(map(str.istitle,text3))
    print(f'text č.:{text} má: {VelP_slova} slov',
    'začinájících velkým písmenem')
#Počet slov psaných velkými písmeny:
    slova_s_VelP = sum(map(str.isupper,text3))
    print(f'text č.:{text} má: {slova_s_VelP} slov',
    'psaná velkými písmeny')
#Počet slov psaných malými písmeny:
    slova_s_MalP = sum(map(str.islower,text3))
    print(f'text č.:{text} má: {slova_s_MalP} slov',
    's malými písmeny')
#Počet čísel:
    cisla = sum(map(str.isdigit,text3))
    print(f'text č.:{text} má: {cisla} čísel')
#Součet čísel:
    cisla1 = []
    soucet = 0
    for cis in text3:
        if cis.isdigit():
            cisla1.append(cis)
    for cis1 in cisla1:
        soucet += int(cis1)
    print(f'součet čísel v textu č.:{text} je: {soucet}\n')
    print(oddelovac_1)

#####
#délky slov vtextu 3:
    cisty_text = []
    rozdeleny_text = text3
    for slovo in rozdeleny_text:
        cisty_text.append(slovo.strip('0123456789').lower())
#délka slov
    delka_slov = []
    for slovo in cisty_text:
        delka_slov.append(len(slovo))
######
    pocet = dict()
    for slovo in delka_slov:
        if slovo not in  pocet:
            pocet[slovo] = 1
        else:
            pocet[slovo] = pocet[slovo] + 1
    del pocet[0]
#seřazení
    serazeny_vysledek = sorted(pocet.keys())
    vysledky = []
    for vyskyt in pocet:
        vysledky.append((pocet[vyskyt],vyskyt))
    print(f'Počet písmen slova  |   četnost slov  ')
    print(oddelovac)
    serazeny_vysledek = sorted(vysledky,reverse = True)
    for index, tupl in enumerate(serazeny_vysledek):
        print(f" {tupl[1]}         {tupl[0]*'*'}     {tupl[0]}x")
