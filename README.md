# Tester przewodow USB
## Wstęp:
Jako projekt wstępnie wybrano tester przewodów USB. Wymagania przyjęte do tego projektu były następujące: stosunkowo niski koszt, prostota obsługi, kompaktowość i wszechstronność. Zdecydowano się, aby tester przeznaczony był dla przewodów USB type C - USB type C. Po podłączeniu przewodów do urządzenia  powinno ono podświetleniem poszczególnych diod ukazywać w jakim trybie może działać dany przewód, oraz możliwe uszkodzenia i cięcia budżetowe producenta w jego strukturze. 

## Założenia projektu:
* Możliwość testu 2 typów przewodów: USB A -> USB C oraz USB C -> USB C
* Dwa tryby częstotliwości pracy układu
* Kompaktowość urządzenia
* Niska cena
  
## Schemat i projekt układu
Wstępny zamysł projektu był następujący. Odpowiednio zaprojektowany system zegara CLK oparty o układ scalony NE555. Następnie sygnał ten przechodzi na 5 przerzutników typu JK działających w układzie licznika synchronicznego od 0 - 24, dzięki czemu możliwe było obsłużenie wszystkich 25 sygnałów pełnego złącza USB type C (a dokładniej 24 pinów sygnałowych oraz shielda). W ten sposób zaprojektowano układ licznika 5 bitowego. Sygnał z poszczególnych wyjść liczników trafia na dwa 4 bitowe dekodery połączone w odpowiedni sposób, zamiast na jeden dekoder 5 bitowy. Wynika to z faktu dostępności i ceny. Układ dwóch 4 bitowych dekoderów jest tańszy i łatwiej dostępny. Sygnał z poszczególnych wyjść dekoderów trafiał na odpowiednie mosfety typu P, a one po otrzymaniu sygnału załączeniowego (logiczne “0”) zaczynały przewodzić do odpowiedniego pinu złącza USB C. Następnie przez przewód sygnał trafiał na odpowiednie szeregowo połączone rezystory i diody, które zaczynały świecić, sygnalizująć działanie danego pinu.

![image](https://github.com/Rocetex/Tester-przewodow-USB/assets/164247771/b01f14ee-7cf3-4f50-aa64-9a80114b79fa)

## Instrukcja obsługi:
Płytkę należy zasilić napięciem 5V. 
Switch S1 odowiada za resetowanie układu.
Przełącznik S3 odpowiada za wybranie częstotliwości pracy układu
Przełącznik S4 odpowiada za wybranie trybu pracy:
1) USB typu A
2) 2) USB typu C
Aby przetestować przewód USB A -> USB C:
- Podłączyć zasilanie do płytki
- Ustawić oczelowamą częstotliwość pracy układu
- Ustawić tryb pracy na USB A
- Wpiąć przewód z złącze USB A (oznaczone na płytce jako J3) oraz w wyjściowe złącze USB typu C (J2)
Aby przetestować przewód USB C -> USB C:
- Podłączyć zasilanie do płytki
- Ustawić oczelowamą częstotliwość pracy układu
- Ustawić tryb pracy na USB C
- Wpiąć przewód z złącze USB C (oznaczone na płytce jako J1) oraz w wyjściowe złącze USB typu C (J2)

## Błędy w konstrukcji płytki:
- Kondensator C3 należy przylutować równolegle do masy oraz do zwartych padów miejsca kondensatora
- Pomimo wykonania symulacji zauważono problem z zamykaniem się mosfetów, z tego powodu zaleca się użycie tranzystorów PNP oraz rezystorów na bramce 1k Ohm

## Prezentacja układu:
![image](https://github.com/Rocetex/Tester-przewodow-USB/assets/164247771/3bd79a89-00ae-4dd4-a149-51382da346e9)
![image](https://github.com/Rocetex/Tester-przewodow-USB/assets/164247771/ad754ebf-3826-4b5f-91ed-f801fcbd2afb)
![image](https://github.com/Rocetex/Tester-przewodow-USB/assets/164247771/d0cae84b-b4d1-4df5-bda9-ae3af1804183)


