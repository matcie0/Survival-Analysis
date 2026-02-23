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


## Projekt 2: Estymacja nieparametryczna i analiza porównawcza

Druga część portfolio koncentruje się na metodach nieparametrycznych, pozwalających na analizę funkcji przeżycia bez narzucania założeń co do rozkładu bazowego danych.

**[Pobierz pełne Sprawozdanie w PDF](./survival-nonparametric-estimation/raport2.pdf)**

#### Zadania i zastosowane metody:

* **Estymacja funkcji przeżycia:**
    * Implementacja estymatora **Kaplana-Meiera** oraz estymatora **Fleminga-Harringtona**.
    * Matematyczne porównanie obu podejść oraz wizualizacja krzywych przeżycia dla różnych grup terapeutycznych (Lek A vs Lek B).
* **Analiza długoterminowego przeżycia (Uzupełnianie ogonów):**
    * Zastosowanie propozycji **Browna-Hollandera-Kowara** (BHK) w celu estymacji wartości funkcji przeżycia w obszarach, gdzie występują jedynie dane cenzurowane.
    * Badanie asymptotycznej normalności estymatora Kaplana-Meiera.
* **Estymacja średniego czasu trwania:**
    * Wyznaczanie średniego czasu życia w oparciu o pole pod krzywą przeżycia z uwzględnieniem wykładniczego ogona BHK.
    * Konstrukcja przedziałów ufności dla średniego czasu do wystąpienia zdarzenia (np. progresji choroby) przy różnych horyzontach czasowych $\tau$.
* **Weryfikacja hipotez nieparametrycznych:**
    * Porównywanie krzywych przeżycia za pomocą rodziny testów rangowych.
    * Analiza czułości i porównanie funkcji wagowych $w(t)$ dla testów: **log-rank**, **Gehana-Breslowa**, **Tarone-Ware'a** oraz **Peto-Peto**.
    * Interpretacja różnic w wartościach p-value w kontekście specyfiki danych (różnice wczesne vs. późne) na przykładzie pacjentek z Mayo Clinic.

#### Narzędzia matematyczne:
Estymatory Kaplana-Meiera i Fleminga-Harringtona, metoda Greenwooda, ogon BHK, testy log-rank i Gehana-Breslowa, funkcje wagowe, symulacje stochastyczne.

#### Wykorzystane biblioteki R:
`survival`, `survminer`, `ggsurvfit`, `coin`, `ggplot2`.

## Projekt 3: Modelowanie regresyjne i weryfikacja założeń

Trzecia część portfolio skupia się na zaawansowanym modelowaniu wpływu zmiennych objaśniających na czas przeżycia. Projekt obejmuje implementację modeli parametrycznych, semiparametrycznych oraz procedury automatycznej selekcji zmiennych.

**[Pobierz pełne Sprawozdanie w PDF](./survival-regression-models/raport3.pdf)**

#### Zadania i zastosowane metody:

* **Modele Przyspieszonego Czasu Awarii (AFT):**
    * Implementacja modelu regresji parametrycznej z bazowym rozkładem **Weibulla**.
    * Interpretacja współczynników za pomocą **Time Ratio (TR)** – analiza wpływu wieku, płci i skali ECOG na przyspieszenie lub opóźnienie momentu zdarzenia.
    * Wyznaczanie predykcji prawdopodobieństwa przeżycia dla specyficznych profili pacjentów na podstawie parametrów kształtu i skali.
* **Semiparametryczny Model Coxa (Proporcjonalnych Hazardów):**
    * Estymacja parametrów modelu Coxa i interpretacja **Ilorazów Hazardu (Hazard Ratio - HR)**.
    * Wyznaczanie bazowej funkcji przeżycia $S_0(t)$ oraz bazowej skumulowanej funkcji hazardu $H_0(t)$ metodą **Breslowa**.
    * Weryfikacja założenia o proporcjonalności hazardów poprzez graficzną analizę równoległości logarytmów skumulowanych funkcji hazardu.
* **Model Proporcjonalnych Szans (PO):**
    * Implementacja modelu PO jako alternatywy dla modelu Coxa w sytuacjach, gdy wpływ cech na ryzyko słabnie w czasie.
    * Interpretacja wyników za pomocą **Ilorazu Szans (Odds Ratio - OR)** i porównanie z modelem PH.
* **Selekcja zmiennych i porównanie modeli:**
    * Procedura budowy modelu optymalnego przy użyciu metody eliminacji wstecznej (**Backwards Elimination**) opartej na teście ilorazu wiarogodności (LRT).
    * Wykorzystanie kryteriów informacyjnych **AIC** oraz **BIC** do automatycznej selekcji predyktorów.
    * Analiza porównawcza predykcji modeli AFT, PH i PO na danych rzeczywistych.

#### Narzędzia matematyczne:
Regresja Weibulla (AFT), Model Proporcjonalnych Hazardów Coxa (PH), Model Proporcjonalnych Szans (PO), Estymator Breslowa, Test Walda, Test Ilorazu Wiarogodności (LRT), Kryteria AIC/BIC.

#### Wykorzystane biblioteki R:
`survival`, `survminer`, `timereg`, `eha`, `broom`, `knitr`.
