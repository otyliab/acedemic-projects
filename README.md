# acedemic-projects
Wybrane raporty techniczne oraz skrypty analityczne zrealizowane w ramach studiów inżynierii biomedycznej.; Selected technical reports and analytical scripts developed during biomedical engineering studies.

### Cyfrowe Przetwarzanie Sygnałów – Analiza i Detekcja Zespołów QRS w Sygnale EKG

* **Opis:** Implementacja offline zmodyfikowanego algorytmu Pana-Tompkinsa służącego do automatycznej detekcji punktów charakterystycznych (załamków Q, R, S) w surowym sygnale elektrokardiograficznym oraz wyznaczania średniego tętna (Heart Rate).
* **Kluczowe etapy przetwarzania:**
  * Usuwanie składowej stałej (detrending) i filtracja pasmowoprzepustowa 5–15 Hz filtrem IIR Butterwortha (z użyciem funkcji `filtfilt` w celu eliminacji przesunięcia fazowego).
  * Różniczkowanie (różnica w przód) i potęgowanie nieliniowe w celu wzmocnienia zboczy załamka R.
  * Całkowanie w oknie ruchomym (Moving-Window Integration) o szerokości 160 ms (16 próbek dla $f_s = 100$ Hz) w celu wyznaczenia obwiedni sygnału.
  * Detekcja szczytów funkcją `findpeaks` z uwzględnieniem okresu refrakcji (MinPeakDistance = 250 ms) oraz lokalne wyszukiwanie minimów dla załamków Q i S w oknie $\pm 50$ ms wokół piku R.
* **Wyniki:** Algorytm poprawnie zidentyfikował wszystkie piki (uzyskane tętno: 67.61 BPM, zgodne z normą spoczynkową).
* **Wykorzystane narzędzia:** MATLAB (Signal Processing Toolbox), LaTeX (skład raportu).
* **Pliki:** `[Zobacz pełny raport PDF](Analiza-sygnalow/BorodijukOtyliaCPS.pdf)`
