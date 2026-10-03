# Karta Tematu: Alpha221 – Inteligentny optymalizator portfela inwestycyjnego przy zadanym limicie ryzyka

**Zespół 4**
* Kacper Nowaczyk (31838)
* Adam Remfeld (31799)
* Nikodem Boniecki (31865)

## 1. Dla kogo i po co? 
System pomaga inwestorom detalicznym w budowie zdywersyfikowanego portfela akcji (skupionego m.in. na sektorach AI, gamedev i półprzewodników). Rozwiązuje problem skomplikowanego, matematycznego równoważenia zysku i ryzyka, dostarczając automatycznie zoptymalizowane wagi dla wybranych spółek w sposób maksymalizujący potencjalny oczekiwany zwrot przy jednoczesnym zachowaniu twardego limitu ryzyka (nieprzekraczalnego poziomu wariancji/zmienności) zadanego przez użytkownika.

## 2. Która technologia z zakresu laboratorium?
Problem należy do klasy optymalizacji. Rozwiązanie zostanie oparte na autorskiej implementacji algorytmu genetycznego.

## 3. Skąd dane?
Wykorzystamy oficjalne, w pełni legalne API dostarczające wyselekcjonowane dane rynkowe:
* **Nazwa zbioru:** Tiingo End-of-Day (EOD) Stock API
* **Rozmiar:** Dane pobierane dynamicznie w formacie JSON. Zakładamy analizę koszyka ok. 50-100 spółek w horyzoncie 5 lat (rozmiar danych z jednego zapytania to kilka/kilkanaście megabajtów).
* **Licencja:** Tiingo API Free Tier / Internal Use Only (oficjalna, darmowa licencja deweloperska przeznaczona do użytku akademickiego i osobistego).
* **Link:** https://api.tiingo.com/

## 4. Co implementujecie sami?
Samodzielnie implementujemy cały rdzeń sztucznej inteligencji: algorytm genetyczny od zera. Obejmuje to autorskie mechanizmy selekcji, krzyżowania, mutacji oraz funkcję przystosowania (fitness), która będzie promować wyższy zwrot z inwestycji, jednocześnie nakładając silną karę za przekroczenie ustalonego limitu ryzyka. Gotowe biblioteki (takie jak `requests`, `pandas` czy `numpy`) posłużą nam wyłącznie do komunikacji z API Tiingo, przetworzenia danych wejściowych (wyliczenie dziennych stóp zwrotu) oraz wstępnego wyznaczenia macierzy kowariancji.

## 8. Kryterium sukcesu / Punkt odniesienia
Skuteczność naszego algorytmu genetycznego (osiągnięty zwrot przy zadanym limicie ryzyka oraz wydajność obliczeniowa) zostanie sprawdzona na tej samej porcji danych testowych i porównana z dwoma punktami odniesienia:
1. **Model Markowitza (Mean-Variance Optimization)** – jako dokładne, analityczne rozwiązanie eksperckie.
2. **Portfel naiwny (1/N)** – reprezentujący prostą strategię równomiernego podziału kapitału (brak ukierunkowanej optymalizacji ryzyka).