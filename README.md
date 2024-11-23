# metoda Monte Carlo (obliczanie przybliżonej wartości liczby π, symulacja ruchów Browna) 

## 1. Co to jest
**Metoda Monte Carlo** (MC) – metoda stosowana do modelowania matematycznego procesów zbyt złożonych (obliczania całek, łańcuchów procesów statystycznych), aby można było przewidzieć ich wyniki za pomocą podejścia analitycznego. Istotną rolę w tej metodzie odgrywa losowanie (wybór przypadkowy) wielkości charakteryzujących proces, przy czym losowanie dokonywane jest zgodnie z rozkładem, który musi być znany.

### Np:
![POL_województwo_łódzkie_1950](https://github.com/user-attachments/assets/a422d397-c5e3-40e2-a69f-11f41a6b70fd)
Na obrazku przedstawiono obszar Polski z podziałem na województwa. Losowo umieszczono 84 punktów z czego 6 z nich znajduje się w województwie Łódzkim. Szacując metodą Monte Carlo możemy stwierdzić iż województwo Łódzkie stanowi 6/84 (około 7%) powieszni Polski. Czyli 6 / 84 x 322 575 km^2 = 23 041 km^2. Prawdziwa powieszchnia województwa łódzkiego jest jednak równa 18 219 km^2. 
### Zalety:
- Prostota
- Szybkość w otrzymywaniu wyniku
### Wady:
- Różny wynik zalerzny od ilości wylosowanych punktów oraz ich umiejscowienia (za każdym razem wynik bedzie inny)
- Brak dokładnego wyniku

---

## 2. Szacowanie liczby π

- Video wyjaśniające jak metoda Monte Carlo może w łątwy sposób znaleźć liczbe π.
  https://www.youtube.com/watch?v=ELetCV_wX_c

