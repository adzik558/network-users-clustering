# Klasteryzacja użytkowników sieci na podstawie odległości i parametrów (Python)

Projekt polega na symulacji użytkowników sieci (punktów na płaszczyźnie) oraz
ich klasteryzacji na podstawie różnych cech — odległości od routerów (centroidów),
parametru prędkości, opóźnienia (ping) oraz priorytetu. 

Celem projektu jest zademonstrowanie działania algorytmów klasteryzacji oraz
pokazanie, jak dodatkowe atrybuty mogą wpływać na przypisanie punktów do grup.

Projekt został wykonany w języku **Python** w ramach zajęć z inżynierii danych.

---

## Struktura repozytorium


```plaintext
network-traffic-analysis-anomaly-detection/
├── README.md
├── LICENSE
├── requirements.txt
├── docs/
│   └── klasteryzacja - dokumentacja.pdf
├── src/    
│   └── clustering.R          
└── plots/
    ├── ss1.png
    ├── ss2.png
    ├── ss3.png
    ├── ss4.png
    └── ss5.png


```



- **clustering.R** – główny kod projektu
- **klasteryzacja - dokumentacja.pdf** – pełna dokumentacja projektu  
  (opis metod, wyniki, wykresy, wyjaśnienie podejścia) 
- wykresy
  

---

## Cel projektu

Zgodnie z opisem w rozdziale *Cel pracy* (strona 5 PDF), celem było:  
- wygenerowanie losowych punktów reprezentujących użytkowników,  
- zdefiniowanie centrów odpowiadających routerom,  
- sklasteryzowanie tych punktów na różne sposoby:  
  - tylko na podstawie odległości,  
  - w oparciu o prędkość łącza,  
  - w oparciu o ping,  
  - w oparciu o priorytet użytkownika.  

---

##  Zastosowane metody klasteryzacji

W projekcie wykorzystano m.in.:

### Klasteryzacja K-Means
Przykład implementacji znajduje się na stronie 5 PDF — za pomocą scikit-learn
podzielono 1000 punktów na 8 klastrów i wyznaczono centroidy.  

<img width="768" height="426" alt="image" src="https://github.com/user-attachments/assets/d52f87f2-af6b-4c59-b2e3-cefbd6059dd4" />


### Klasteryzacja według najbliższego centroidu
Każdy punkt przydzielany jest do klastra na podstawie najmniejszej odległości,
przy centroidach zdefiniowanych ręcznie.  

<img width="681" height="439" alt="image" src="https://github.com/user-attachments/assets/e12c8214-812c-468b-8e3d-a451d4170efc" />


### Klasteryzacja z uwzględnieniem prędkości i odległości
Punkt ma atrybut prędkości, a centroidy różnią się przepustowością.  
Przypisanie odbywa się z uwzględnieniem zarówno odległości, jak i prędkości.  

<img width="685" height="438" alt="image" src="https://github.com/user-attachments/assets/afdb3d15-f39f-4edf-8126-5da6246fc4e1" />

### Klasteryzacja na podstawie odległości oraz ping'u
Każdy punkt posiada parametr *ping*, a centroid odpowiada zakresowi pingów.  
Punkt trafia do klastra centroidu, którego zakres obejmuje jego wartość.  

<img width="677" height="443" alt="image" src="https://github.com/user-attachments/assets/9a206380-4b3e-490e-9cae-68629cf698e4" />


### Klasteryzacja wg priorytetu i odległości
Punkty posiadają priorytet (0–2), który wpływa na przypisanie do klastra.
Priorytet 0 jest traktowany jako specjalny przypadek — klasteryzacja tylko wg odległości.  

<img width="676" height="430" alt="image" src="https://github.com/user-attachments/assets/0b90f8b2-9cb4-4f30-ba6e-c46378785136" />



---

## Technologie

- Python 3.x  
- NumPy  
- scikit-learn (dla K-Means)  
- matplotlib (wizualizacje)

Kod korzysta z prostych klas (`Point`) oraz ręcznej implementacji logiki klasteryzacji,
co dobrze pokazuje działanie algorytmów od podstaw.  

## Jak uruchomić projekt (krok po kroku)

1. Pobierz plik **src/clustering-ipynb** o
2. Otwórz go np. w Google Colab.
3. Skompiluj komórki:    
4. Gotowe!  
   Wyniki pojawią się poniżej kompilowanych komórek.

