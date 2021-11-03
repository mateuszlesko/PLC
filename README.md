<h1>Projekty PLC</h1>
<div style="margin:40px 40px;">dla platform: Simens S1200 i Simens S300</div>

<h2>Materiał</h2>
<h3>Moduły pamięci</h3>
<h4>Pamięć z dominacją zapisu</h4>
![image](https://user-images.githubusercontent.com/31209474/137718085-6546f971-0c06-4f6d-8254-9408e3ff7442.png)
<h4>Pamięć z dominacją kasowania</h4>
![image](https://user-images.githubusercontent.com/31209474/137719291-2d1c3803-11b9-429b-8a8e-a095a4c8dff4.png)
<h3>Układ: Pompa </h3>
Układ sterownia pompą podłączoną do zbiornika. Pompa ma zadanie pompowac ciecz do zbiornika do poziomu ustalongego przez czujniki. Zbiornik posiada 2 czujniki poziomu cieczy: czujnik1 (dolny stan cieczy), czujnik2 (gorny stan cieczy). Jest to przyklad akademicki, z tego powodu wyodrebniono 2 czujniki stanu cieczy w zbiorniku.<br/>
<b>Tabela stanow pracy pompy</b>
<table border="2px" color="black">
  <th>
    <td>stan niski</td>
    <td>stan średni</td>
    <td>stan wysoki</td>
    <td>AWARIA</td>
  </th>
  <tr>
  <td><b>C0</b></td><td>0</td><td>1</td><td>1</td><td>0</td>
  </tr>
    <tr>
  <td><b>C1</b></td><td>0</td><td>0</td><td>1</td><td>1</td>
  </tr>
    <tr>
  <td><b>P</b></td><td>1</td><td>1 / 0</td><td>0</td><td>0</td>
  </tr>
</table>
Gdzie:
C0 = czujnik poziomu dolnego
C1 = czujnik poziomu gornego
P = pompa
<br/>
<b>Tabela sygnalow wraz z wejsciami i wyjsciami</b>
<table border="2px" color="black">
  <th>
  <td><b>C0 [I0.0]</b></td>
  <td><b>C1 [I0.1]</b></td>
  <td><b>SYGNALIZACJA</b></td>
  <td><b>POMPA [Q1.0]</b></td>
  </th>
  <tr>
  <td></td><td>0</td><td>0</td><td>POZIOM NISKI [Q0.0]</td><td>1</td>
  </tr>
  <tr>
  <td></td><td>1</td><td>0</td><td>POZIOM SREDNI [Q0.1]</td> <td>1/0</td>
  </tr>
  <tr>
  <td></td><td>1</td> <td>1</td> <td>POZIOM WYSOKI [Q0.2]</td> <td>0</td>
  </tr>
  <tr>
  <td></td><td>0</td> <td>1</td> <td>AWARIA [Q0.7]</td> <td>0</td>
  </tr>
</table>

<h4>NETWORK:stan niski</h4>
![image](https://user-images.githubusercontent.com/31209474/140063742-67d26632-d366-4cf4-8d87-a5b73ef9dfcb.png)<br/>
Gdzie: C0 = stan wejscia czujnika poziomu dolnego C1 = stan wejscia czujnika poziomu wysokiego PN = wyjscie poziom niski
<h5>Opis:</h5>
Gdy na wejsciach C0 i C1 panuje stan logiczny 0, oznacza to, ze w zbiorniku poziom cieczy jest na poziomie niskim

<h4>NETWORK:stan sredni</h4>
![image](https://user-images.githubusercontent.com/31209474/140063898-6ee0dc62-983a-4580-9e0d-9d50c98dd8b0.png)<br/>
Gdzie: C0 = stan wejscia czujnika poziomu dolnego C1 = stan wejscia czujnika poziomu wysokiego PS = wyjscie poziom sredni
<h5>Opis:</h5>
Gdy na wejsciach C0 panuje stan logiczny 1 i na C1 panuje stan logiczny 0, oznacza to, ze w zbiorniku poziom cieczy jest na poziomie srednim

<h4>NETWORK: stan wysoki</h4>
![image](https://user-images.githubusercontent.com/31209474/140064533-5330e86a-e3c5-4c51-ac16-f0df820a4aaa.png)<br/>
Gdzie: C0 = stan wejscia czujnika poziomu dolnego C1 = stan wejscia czujnika poziomu wysokiego PNW = wyjscie poziom wysoki
<h5>Opis:</h5>
Gdy na wejsciach C0 i C1 panuje stan logiczny 1, oznacza to, ze w zbiorniku poziom cieczy jest na poziomie wysokim
<h3>UKLAD: przycisk wlaczajacy i wylaczajacy</h3>
Zapisanie stanu w pamieci czy przycisk byl zalaczony, wykorzystanie zbocza gornego do potrzymania stanu wyjsciowego na jego wejscie

<h4>NETWORK: awaria</h4>
![image](https://user-images.githubusercontent.com/31209474/140066466-64726e65-7aa6-4834-ae3b-b65c952cd7e2.png)<br/>
Gdzie: C0 = stan wejscia czujnika poziomu dolnego C1 = stan wejscia czujnika poziomu wysokiego A = wyjscie awaria
<h5>Opis:</h5>
Gdy na wejsciu C0 panuje stan logiczny 0 i na C1 panuje stan logiczny 1, oznacza to, ze uklad ulegl awarii

<h4>NETWORK: praca pompy</h4>
![image](https://user-images.githubusercontent.com/31209474/140067491-d3440dac-32cb-465f-af82-72f0e57b9b01.png)<br/>
Gdzie: PN = wejscie gdzie sygnal podany to wyjscie networkingu stanu niskiego PS = wejscie gdzie sygnal podany to wyjscie networkingu stanu sredniego
PRACA = zbocze gorne, podtrzymanie stanu pracy pompy
<h5>Opis:</h5>
Gdy na wejsciu PN panuje stan logiczny 1 lub na wejsciu PS panuje stan logiczny 1, podtrzymaj stan 1 na wyjsciu - pompa pracuje.

<h4>NETWORK: zatrzymanie pracy pompy</h4>
![image](https://user-images.githubusercontent.com/31209474/140068070-bba1e95e-bb55-4ab8-8629-a7992e275c19.png)<br/>
Gdzie: A = wejscie gdzie sygnal podany to wyjscie networkingu awarii PW = wejscie gdzie sygnal podany to wyjscie networkingu stanu wysokiego
PRACA = reset podtrzymania stanu pracy pompy
<h5>Opis:</h5>
Gdy na wejsciu PW panuje stan logiczy 1 lub gdy na wejsciu A panuje stan logiczny A,zresetuj podtrzymanie stanu logicznego 1 na wyjsciu - pompa nie pracuje

<h4>NETWORK: sygnalizacja awarii</h4>
![image](https://user-images.githubusercontent.com/31209474/140068638-53f5f70e-7c5e-4d2f-a57b-9299eb502383.png)<br/>
Gdzie: ZA = zbocze awarii, PA = pamiec awarii
<h5>Opis:</h5>
Gdy na wejsciu zbocza awarii panuje stan 1, ustaw w komorce pamieci stan logiczny 1 dla zdarzenia awarii

<h4>NETWORK: pamieci awarii</h4>
![251990523_568041074267139_7882462613094481930_n](https://user-images.githubusercontent.com/31209474/140071106-4004eb04-6a26-4e1c-bd36-3bb387baefda.jpg)<br/>
Gdzie: awaria = podanie i odtrzymanie wartosci wyjscia networkingu awaria przy uzyciu zbocza górnego; zboczeAwarii = wartosc do odczytu z pamieci spod adresu M12.0; pAwarii = pamięć awarii - zapisanie stanu do komorki M14.0
<h5>Opis</h5>
Na wejscie podawany jest stan wyjscia networkingu awaria i dane z komorki M12.0 przechowujacej wartosc podtrzymania stanu awarii poprzez uzycie zbocza. Zaleznie od wejscia do pamieci pod adres M14.0 zostanie zapamietany sygnal awarii 

<h4> NETWORK: Sygnalizacja awarii przy uzyciu zegara / generatora</h4>
![251990523_568041074267139_7882462613094481930_n](https://user-images.githubusercontent.com/31209474/140072760-a8c49650-aa63-41c8-bd7a-fe9ab22c0890.jpg)<br/>
Gdzie:
pAwarii = pamiec awarii pod adresem M14.0; Clock_1Hz = zegar ustawiony na czestostliwosc 1s; awaria = podanie stanu wyjscia networkingu awaria;
sygAwaria = wyjscie pod adresem Q0.7 sygnalizujace awarie.
<h5>Opis</h5>
Jesli pole pAwarii (adres komorki w pamieci) i sygnal zegara przyjmuja wartosc 1 lub jesli pole wyjsciowe networkingu awaria i pole pAwarii przyjmuja wartosc 1, to zasygnalizuj awarie 

<h3>UKŁAD: przycisk włączajacy i wyłączający</h3>
Zapisanie stanu w pamieci czy przycisk byl załączony, wykorzystanie zbocza górnego do podtrzymania stanu
