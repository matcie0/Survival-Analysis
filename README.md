# Survival-Analysis
Analiza danych cenzurowanych i modelowanie czasu trwania zdarzeń. Implementacja estymatorów Kaplana-Meiera, testów log-rank oraz modeli Coxa i AFT w języku R.

## Projekt 1: Symulacja danych i estymacja parametryczna

Pierwsza część portfolio skupia się na implementacji probabilistycznych modeli czasu trwania oraz statystycznej weryfikacji estymatorów w warunkach niepełnej informacji.

**[Pobierz pełne Sprawozdanie w PDF](./survival-analysis-simulations-and-testing/raport1.pdf)**

#### Zadania i zastosowane metody:

* **Modelowanie rozkładu Exponentiated-Weibull (EW):**
    * Implementacja numeryczna funkcji gęstości, dystrybuanty oraz funkcji kwantylowej.
    * Analityczne wyznaczenie funkcji hazardu $h(t)$ i analiza jej przebiegu (malejący, stały, dzwonkowy, wannowy) dla różnych parametrów kształtu $\alpha$, $\beta$ i $\gamma$.
* **Generowanie danych cenzurowanych:**
    * Symulacja zmiennych losowych z ogólnionego rozkładu wykładniczego.
    * Implementacja mechanizmów cenzurowania: typu I, typu II oraz losowego.
* **Wnioskowanie statystyczne:**
    * Wyznaczanie estymatorów największej wiarygodności (MLE) dla parametru intensywności $\theta$ i średniego czasu $\mu$.
    * Konstrukcja przedziałów ufności w oparciu o rozkład Gamma (dla cenzurowania typu II) oraz metody dokładne dla rozkładu dwumianowego.
* **Weryfikacja hipotez i analiza mocy testu:**
    * Implementacja testu ilorazu wiarygodności (LRT) dla danych cenzurowanych.
    * Ocena jakości estymatorów poprzez wyznaczenie obciążenia oraz błędu średniokwadratowego (MSE) metodą Monte Carlo.
    * Empiryczne wyznaczenie mocy testu i poziomu istotności dla różnych liczebności próby.

#### Narzędzia matematyczne:
Rozkłady EW i GE, Estymacja Największej Wiarygodności (MLE), Test Ilorazu Wiarygodności (LRT), statystyki porządkowe, symulacje stochastyczne.

#### Wykorzystane biblioteki R:
`survival`, `binom`, `knitr`, `kableExtra`.
