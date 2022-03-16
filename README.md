# Projekty PLC:

Repozytorium zawiera zestaw zadań zrealizowanych na laboratorium komputerowych systemów sterowania.

Model PLC na którym zostały wykonane zadania to: Siemens S1200 DC/DC/DC. 

Język wykorzystywany do programowania kontrolera : LAD

## Materiał
### lab2: Moduły pamięci
* pamięć z dominacją zapisu
* pamięć z dominacją kasowania

Networki projektu:
[Pamieci](lab2Pamieci/lab.pdf) 

### lab3 
#### Podzielnik binary
Podzielnik binarny służy do zapisanie stanu poprzedniego w pamieci, dzięki czemu można zrealizować 2 mechaniki przy pomocy 1 przycisku - włącz / wyłącz (załącz / rozłącz)

Networki: 1 - 2

#### Wykrywanie kierunku: (lewo czy prawo)

Zbocze narastające na I0.2 (czujnik lewy) + 1 na I0.3 (czujnik prawy) = kierunek lewo

Zbocze narastające na I0.3 (czujnik prawy) + 1 na I0.2 (czujnik lewy) = kierunek prawo 
Networki: 3 - 4

#### Wykrywanie długości belki : krótka / średnia / długa

Ocena długości belki poprzez użycie 3 czujników:
* czujnika dla krótkiej długości
* czujnika dla średniej długości
* czujnika dla długiej długości

Wykrycie zbocza narastającego na I0.3 informuje, że jest to co najmniej krótka belka, informacja o tym zapisywana jest do pamięci

"1" w komórce odpowiedzialnej za przechowywanie informacji o co najmniej krótkiej długości i zbocze narastające na I0.4 informuje, że jest to co najmniej średnia belka, infromacja o tym zapisywana jest do pamięci

"1" w komórce odpowiedzialnej za przechowywanie informacji o co najmniej średniej długości i zbocze narastające na I0.5 informuje, że jest to co najmniej długa belka, infromacja o tym zapisywana jest do pamięci

Następnie wartości z pamięci są podawana na wyjścia sterownika

Networki : 5 - 10

Networki projektu:
[Pamieci](lab3/lab.pdf) 

### lab4: Generatory:
#### Generator szplikowy:
Szpilka (stan logicznej 1) przez urywek czasu - trwa zależnie od częstotliwości procesora.
Szpilka pojawia się co zadany okres czasu

Network : 1 - 2

#### Generator na bazie TON - TON
Generator ma określoną przerwę oraz czas impulsu

Liczenie okresu:
T = 1/f
T = TON dla opóźnienia + TON dla sygnału (wypełnienie)

Network 3 - 4

#### Generator na bazie TON - TP
Generator o zadanym wypełnieniu, użycie timera TON powoduje opóźnienie sygnału, zaś TP powoduje impuls stały o zadanej długości - wypełenienie sygnału

Network 5 - 6

Networki projektu:
[Generatory](lab4/lab.pdf) 


### lab6.5 = Generatory ciąg dalszy:

#### Zadanie:
zbuduj generator pracujacy na wyj q1.0 w nastepujacy sposob generuje 10 impulsow o f = 2Hz i 5 impulsow o f 0.5 Hz

Wyliczenie okresu:

T = 1/f

f1 = 2 Hz; f2 = 0.5Hz

T1 = 1/2 Hz = 0.5s

T2 = 1/(0.5 Hz) = 2s

Networki projektu:
[Generator zadanie](lab6.5/lab.pdf)