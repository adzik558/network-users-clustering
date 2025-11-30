# Klasteryzacja użytkowników sieci na podstawie odległości i parametrów (Python)

Projekt polega na symulacji użytkowników sieci (punktów na płaszczyźnie) oraz
ich klasteryzacji na podstawie różnych cech — odległości od routerów (centroidów),
parametru prędkości, opóźnienia (ping) oraz priorytetu. 

Celem projektu jest zademonstrowanie działania algorytmów klasteryzacji oraz
pokazanie, jak dodatkowe atrybuty mogą wpływać na przypisanie punktów do grup.

Projekt został wykonany w języku **Python** w ramach zajęć z inżynierii danych.

---

## Struktura repozytorium


```plaintextnetwork-traffic-analysis-anomaly-detection/
├── README.md
├── LICENSE
├── requirements.txt
├── requirements_R.txt      
├── data/
│   └── sample_traffic.csv
├── docs/
│   └── klasteryzacja - dokumentacja.pdf
├── src/    
│   └── clustering.R            
├── plots/
│   └── example_plot.png    
└── tests/
    └── test_data_check.R   
```
- **clustering_users.ipynb / clustering.py** – główny kod projektu
- **Klasteryzacja.pdf** – pełna dokumentacja projektu  
  (opis metod, wyniki, wykresy, wyjaśnienie podejścia) 
- przykładowe wykresy (opcjonalnie)

Dokumentacja szczegółowo opisuje wszystkie zastosowane metody
(Albo: *Plik Klasteryzacja.pdf zawiera pełny opis implementacji — generowanie punktów,
definicje klas, algorytm K-Means, klasteryzację z prędkością, pingiem i priorytetem*).  

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

### Klasteryzacja według najbliższego centroidu
Każdy punkt przydzielany jest do klastra na podstawie najmniejszej odległości,
przy centroidach zdefiniowanych ręcznie.  

### Klasteryzacja z uwzględnieniem prędkości
Punkt ma atrybut prędkości, a centroidy różnią się przepustowością.  
Przypisanie odbywa się z uwzględnieniem zarówno odległości, jak i prędkości.  

### Klasteryzacja na podstawie ping
Każdy punkt posiada parametr *ping*, a centroid odpowiada zakresowi pingów.  
Punkt trafia do klastra centroidu, którego zakres obejmuje jego wartość.  

### Klasteryzacja wg priorytetu
Punkty posiadają priorytet (0–2), który wpływa na przypisanie do klastra.
Priorytet 0 jest traktowany jako specjalny przypadek — klasteryzacja tylko wg odległości.  
---

## Technologie

- Python 3.x  
- NumPy  
- scikit-learn (dla K-Means)  
- matplotlib (wizualizacje)

Kod korzysta z prostych klas (`Point`) oraz ręcznej implementacji logiki klasteryzacji,
co dobrze pokazuje działanie algorytmów od podstaw.  
