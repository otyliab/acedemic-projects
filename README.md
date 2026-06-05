# acedemic-projects
Wybrane raporty techniczne oraz skrypty analityczne zrealizowane w ramach studiów inżynierii biomedycznej.; 
Selected technical reports and analytical scripts developed during biomedical engineering studies.

PL:

### Cyfrowe Przetwarzanie Sygnałów – Analiza i Detekcja Zespołów QRS w Sygnale EKG

* **Opis:** Implementacja offline zmodyfikowanego algorytmu Pana-Tompkinsa służącego do automatycznej detekcji punktów charakterystycznych (załamków Q, R, S) w surowym sygnale elektrokardiograficznym oraz wyznaczania średniego tętna (Heart Rate).
* **Kluczowe etapy przetwarzania:**
  * Usuwanie składowej stałej (detrending) i filtracja pasmowoprzepustowa 5–15 Hz filtrem IIR Butterwortha (z użyciem funkcji `filtfilt` w celu eliminacji przesunięcia fazowego).
  * Różniczkowanie (różnica w przód) i potęgowanie nieliniowe w celu wzmocnienia zboczy załamka R.
  * Całkowanie w oknie ruchomym (Moving-Window Integration) o szerokości 160 ms (16 próbek dla $f_s = 100$ Hz) w celu wyznaczenia obwiedni sygnału.
  * Detekcja szczytów funkcją `findpeaks` z uwzględnieniem okresu refrakcji (MinPeakDistance = 250 ms) oraz lokalne wyszukiwanie minimów dla załamków Q i S w oknie $\pm 50$ ms wokół piku R.
* **Wyniki:** Algorytm poprawnie zidentyfikował wszystkie piki (uzyskane tętno: 67.61 BPM, zgodne z normą spoczynkową).
* **Wykorzystane narzędzia:** MATLAB, LaTeX.
* **Pliki:** `[Zobacz pełny raport PDF](Analiza-sygnalow/BorodijukOtyliaCPS.pdf)`

ENG: 

### Digital Signal Processing – QRS Complex Detection in ECG Signals

* **Description:** Offline implementation of a modified Pan-Tompkins algorithm for automated detection of ECG characteristic points (Q, R, S waves) and heart rate (HR) calculation.
* **Key Processing Stages:**
  * DC component removal (detrending) and 5–15 Hz bandpass filtering using a 2nd-order IIR Butterworth filter (processed via `filtfilt` for zero-phase distortion).
  * Differentiation (forward difference) and non-linear squaring to amplify the slopes of the R-peaks and suppress background noise.
  * Moving-Window Integration (MWI) using a 160 ms window width (16 samples at $f_s = 100$ Hz) to obtain the signal envelope.
  * Peak detection using `findpeaks` with an implemented refractory period (MinPeakDistance = 250 ms) and local window searching ($\pm 50$ ms) for precise Q and S wave localization.
* **Results:** Successful detection of all wave components across varying signal amplitudes, yielding a resting heart rate of 67.61 BPM.
* **Tools Used:** MATLAB (Signal Processing Toolbox), LaTeX (report typesetting).
* **Files:** `[View Full Report PDF](Analiza-sygnalow/BorodijukOtyliaCPS.pdf)`
