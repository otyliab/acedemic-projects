# acedemic-projects
Wybrane raporty techniczne oraz skrypty analityczne zrealizowane w ramach studiów inżynierii biomedycznej.; 
Selected technical reports and analytical scripts developed during biomedical engineering studies.

---

### Language / Język
* [Kliknij tutaj, aby przeczytać opis po polsku](#-wersja-polska)
* [Click here to read the description in English](#-english-version)

---

## Wersja Polska

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

### Analiza Regresyjna i Aproksymacja Danych Pomiarowych (OriginPro vs MS Excel)

* **Opis:** Porównawcza analiza zaawansowanych metod regresji liniowej, wielomianowej oraz nieliniowej dla zbiorów danych obarczonych szumem pomiarowym, zrealizowana równolegle w środowiskach OriginPro oraz Microsoft Excel.
* **Kluczowe etapy i zagadnienia:**
  * **Regresja liniowa i wielomianowa II stopnia:** Wyznaczenie równań dopasowania metodą najmniejszych kwadratów i weryfikacja jakości modeli za pomocą współczynnika determinacji $R^2$.
  * **Analiza modeli nieliniowych:** Testowanie zaawansowanych funkcji eksponencjalnych w OriginPro (m.in. jednofazowego zaniku `ExpDecay1` oraz dwufazowego `ExpDec2`) i zestawienie ich z podstawową linią trendu logarytmicznego w Excelu.
  * **Weryfikacja formatów graficznych:** Analiza porównawcza przydatności eksportu wykresów do formatów rastrowych (PNG) oraz skalowalnych formatów wektorowych (EMF) pod kątem zachowania ostrości i estetyki dokumentacji technicznej.
* **Wyniki:** Wykazano przewagę dedykowanych narzędzi OriginPro w analizie nieliniowej, gdzie model biexponential (`ExpDec2`) pozwolił na uzyskanie idealnego dopasowania ($R^2 = 1.0$), podczas gdy uproszczony model logarytmiczny z Excela osiągnął wynik $R^2 = 0.98$.
* **Wykorzystane narzędzia:** OriginPro (Polynomial Fit, Non-linear Curve Fitting), MS Excel, LaTeX (skład raportu).
* **Pliki:** `[Zobacz pełny raport PDF](Analiza-Spektroskopowa/BorodijukOtylia1.pdf)`

### Analiza Danych Spektroskopowych – Dekonwolucja Widma Układu Wieloskładnikowego

* **Opis:** Analiza jakościowa i ilościowa widm absorpcyjnych UV-Vis barwników roślinnych w złożonej matrycy biologicznej (tkanka liścia) oraz próbkach środowiskowych.
* **Kluczowe etapy przetwarzania i analizy:**
  * Wyznaczanie charakterystycznych parametrów spektralnych głównego pasma absorpcji (maksimum $\lambda_{max} = 684.43$ nm, intensywność $I = 82.54\%$) przy użyciu metodyki transformacji skali pikselowej na jednostki fizyczne.
  * Wyznaczanie szerokości połówkowej pasma ($\Delta\vartheta_{1/2} = 62.69$ nm) z uwzględnieniem nachylenia linii bazowej w celu separacji tła optycznego.
  * Matematyczny rozkład (dekonwolucja) zbiorczego widma absorpcyjnego na 5 składowych pasm (z wykorzystaniem profili Gaussa/Lorentza) w celu identyfikacji i separacji sygnałów chlorofilu a, chlorofilu b oraz barwników pomocniczych.
  * Kwantyfikacja stężenia i masy chlorofilu a w próbkach wodnych na podstawie prawa Lamberta-Beera oraz analiza błędów metodologicznych związanych z addytywnością absorpcji i doborem długości fali pomiarowej (658 nm vs 684 nm).
* **Wyniki:** Wyznaczono średnią zawartość chlorofilu w badanej wodzie morskiej ($0.0171$ g/dm³) oraz wykazano krytyczny wpływ dekonwolucji na dokładność oznaczania składników w układach wieloskładnikowych.
* **Wykorzystane narzędzia:** OriginPro (analiza graficzna, dopasowanie linii bazowej), LaTeX (skład raportu).
* **Pliki:** `[Zobacz pełny raport PDF](Analiza-spektroskopowa/BorodijukOtylia6.pdf)`

## English Version

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

### Spectroscopic Data Analysis – Spectrum Deconvolution of a Multi-Component System

* **Description:** Qualitative and quantitative UV-Vis spectroscopic analysis of plant pigments within a complex biological matrix (leaf tissue) and environmental water samples.
* **Key Processing Stages:**
  * Determination of core spectral parameters (spectral maximum $\lambda_{max} = 684.43$ nm, intensity $I = 82.54\%$) using pixel-to-unit scale transformation.
  * Full Width at Half Maximum ($\Delta\vartheta_{1/2} = 62.69$ nm) calculation incorporating baseline slope correction to isolate background optical noise.
  * Mathematical deconvolution of the bulk absorption spectrum into 5 independent sub-bands (using Gauss/Lorentz profiling) to resolve overlapping signals of chlorophyll a, chlorophyll b, and accessory pigments.
  * Quantitative determination of chlorophyll a concentration using the Beer-Lambert law, followed by a methodological error analysis regarding signal additivity and optimal wavelength selection (658 nm vs. 684 nm).
* **Results:** Calculated the mean chlorophyll concentration in seawater samples ($0.0171$ g/dm³) and demonstrated the necessity of spectral deconvolution for reliable component quantification.
* **Tools Used:** OriginPro (graphical analysis, baseline fitting), LaTeX (report typesetting).
* **Files:** `[View Full Report PDF](Analiza-spektroskopowa/BorodijukOtylia6.pdf)`

### Regression Analysis and Data Approximation (OriginPro vs. MS Excel)

* **Description:** A comparative analysis of linear, polynomial, and non-linear regression techniques applied to noisy experimental datasets, executed within OriginPro and Microsoft Excel[cite: 3].
* **Key Components:**
  * **Linear & 2nd-Order Polynomial Regression:** Curve fitting via the least squares method and evaluation of goodness-of-fit using the coefficient of determination ($R^2$).
  * **Non-Linear Model Evaluation:** Testing advanced exponential decay functions in OriginPro (e.g., single-phase `ExpDecay1` and biexponential `ExpDec2`) against Excel’s standard logarithmic trendline.
  * **Graphic Export Analysis:** Performance comparison between raster (PNG) and scalable vector (EMF) formats regarding image sharpness, pixelation resistance, and technical reporting aesthetics.
* **Results:** Demonstrated OriginPro's superiority in handling non-linear data; the biexponential model (`ExpDec2`) yielded perfect optimization ($R^2 = 1.0$), whereas Excel’s simplified logarithmic approach limited accuracy to $R^2 = 0.98$.
* **Tools Used:** OriginPro (Polynomial Fit, Non-linear Curve Fitting), MS Excel, LaTeX (report typesetting).
* **Files:** `[View Full Report PDF](Metody_Regresji/BorodijukOtyliaSprawozdanie1.pdf)`
