# metoda Monte Carlo (obliczanie przybliżonej wartości liczby π, symulacja ruchów Browna) 

## 1. Co to jest?
Metoda Monte Carlo została opracowana między innymi przez polskiego naukowca Stanisława Ulama oraz węgiersko — amerykańskiego naukowca Johna von Neumanna. Wykorzystano ją podczas prac nad bombą jądrową w celu symulacji procesu rozpadu jąder cząsteczek. Proces był na tyle skomplikowany, że zastosowanie klasycznych modeli obliczeniowych nie zdawało egzaminu.

Metoda polega na przeprowadzeniu procesu w losowy sposób, zakładając, że po wystarczająco dużej liczbie prób otrzymamy wynik zbliżony do rzeczywistego.

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
- przybliżenie π można obliczyć:
  
  **π = 4 x liczba punktów w okregu / liczba wszystkich punktów** 
- Video wyjaśniające jak metoda Monte Carlo może w łątwy sposób znaleźć liczbe π.
  https://www.youtube.com/watch?v=ELetCV_wX_c
  
### Implementacja w Pythonie
```python
import random
import matplotlib.pyplot as plt

def monte_carlo_pi_with_visualization(num_points):
    inside_circle = 0
    points_inside = []
    points_outside = []

    for _ in range(num_points):
        x, y = random.uniform(-1, 1), random.uniform(-1, 1)
        if x**2 + y**2 <= 1:  # Punkt wewnątrz okręgu
            inside_circle += 1
            points_inside.append((x, y))
        else:
            points_outside.append((x, y))

    # Przybliżenie liczby π
    pi_estimate = 4 * (inside_circle / num_points)

    # Wizualizacja
    plt.figure(figsize=(6, 6))
    plt.scatter(*zip(*points_inside), color="blue", s=1, label="Inside Circle")
    plt.scatter(*zip(*points_outside), color="red", s=1, label="Outside Circle")
    plt.gca().set_aspect('equal', adjustable='box')
    plt.title(f"Monte Carlo Approximation of π\nEstimate: {pi_estimate:.5f} (Points: {num_points})")
    plt.legend()
    plt.show()

    return pi_estimate

# Przykład użycia
num_points = 10_000  # Liczba punktów do wygenerowania
pi_approximation = monte_carlo_pi_with_visualization(num_points)
```

#### Pętla `for _ in range(num_points)` - generuje losowy punkt i przypisuje do koła lub nie:
```python
for _ in range(num_points):
        x, y = random.uniform(-1, 1), random.uniform(-1, 1)
        if x**2 + y**2 <= 1:  # Punkt wewnątrz okręgu
            inside_circle += 1
            points_inside.append((x, y))
        else:
            points_outside.append((x, y))
```

#### Szacowanie wartości π na podstawie wylosowanych punktów:
``` python
 # Przybliżenie liczby π
    pi_estimate = 4 * (inside_circle / num_points)
```
#### Wizualizacja graficzna:
``` python
# Wizualizacja
    plt.figure(figsize=(6, 6))
    plt.scatter(*zip(*points_inside), color="blue", s=1, label="Inside Circle")
    plt.scatter(*zip(*points_outside), color="red", s=1, label="Outside Circle")
    plt.gca().set_aspect('equal', adjustable='box')
    plt.title(f"Monte Carlo Approximation of π\nEstimate: {pi_estimate:.5f} (Points: {num_points})")
    plt.legend()
    plt.show()
```

#### Przykłady:
* dla `num_points` = 100
  
  ![image](https://github.com/user-attachments/assets/c13eacec-7a3b-4640-925b-7bb79f28ba41)

* dla `num_points` = 1000

  ![image](https://github.com/user-attachments/assets/3f97ba14-45d0-4ffb-8af6-e61d1cddcd38)

* dla `num_points` = 10000

  ![image](https://github.com/user-attachments/assets/ce812189-5b66-4923-a69a-647505255611)

---

## 3. Ruchy Browna

### Co to?
**Ruchy Browna** (o których możesz przeczytać m.in. w e‐materiale Modelowanie ruchów Browna) zostały opisane — niezależnie — przez Alberta Einsteina, w  roku oraz przez polskiego fizyka Mariana Smoluchowskiego, w  roku. Ich nazwa pochodzi od botanika Roberta Browna, który pod mikroskopem zaobserwował chaotyczne ruchy pyłku kwiatowego. Ruchy Browna powodowane są nieustannym zderzaniem się cząsteczek płynu w danym ośrodku. Przykładowy model takiego procesu może polegać na umieszczeniu wirtualnej cząsteczki w wirtualnym płynie, w którym — co pewien określony czas — cząsteczka zostaje przemieszczona w losowym kierunku, w wyniku wirtualnej kolizji. Cały proces ma charakter uśredniony. Dzięki temu każda kolizja powoduje przesunięcie cząsteczki o określoną z góry odległość.

Wizualizacja - https://www.youtube.com/shorts/Vm_UlcS4FJE



  



