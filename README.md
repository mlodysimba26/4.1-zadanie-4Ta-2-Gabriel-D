# Minutnik Pomodoro

Aplikacja webowa odliczająca czas sesji pracy i przerw zgodnie z techniką Pomodoro, stworzona na podstawie promptu demonstracyjnego.

## Rozbiór promptu z pokazu

Poniżej znajduje się treść promptu demonstracyjnego użytego do wygenerowania aplikacji minutnika, z podziałem i oznaczeniem każdej linii pod kątem roli w poleceniu:

1. `Stwórz aplikację webową minutnika do techniki Pomodoro.`  
   -> **[Co ma powstać]** (określenie typu tworzonej aplikacji i jej głównego przeznaczenia)

2. `Minutnik powinien domyślnie odliczać 25 minut pracy oraz 5 minut krótkiej przerwy.`  
   -> **[Co ma powstać]** (definicja podstawowych interwałów czasowych i trybów)

3. `Po każdych 4 ukończonych cyklach pracy aplikacja ma przełączać się na długą przerwę trwającą 15 minut.`  
   -> **[Co ma powstać]** (logika przejścia w dłuższą przerwę po określonej liczbie powtórzeń)

4. `Interfejs powinien zawierać duży wyświetlacz cyfrowy czasu w formacie MM:SS, etykietę aktualnego stanu oraz wskaźnik ukończonych cykli (np. 4 kropki).`  
   -> **[Co ma powstać]** (opis wymaganych elementów wizualnych interfejsu użytkownika)

5. `Dodaj panel sterowania z trzema przyciskami: Start, Pauza i Reset.`  
   -> **[Co ma powstać]** (zestaw elementów kontrolnych do interakcji)

6. `Napisz całość w jednym pliku index.html ze stylami CSS w sekcji <style> i logiką JavaScript w sekcji <script>.`  
   -> **[Jak]** (gdzie ma znaleźć się plik oraz struktura osadzenia kodu)

7. `Użyj czystego języka JavaScript (Vanilla JS), bez żadnych zewnętrznych bibliotek, bundlerów czy frameworków.`  
   -> **[Jak]** (wybór technologii i ograniczenie narzędziowe)

8. `Zadbaj o nowoczesny, minimalistyczny wygląd CSS z płynnymi przejściami kolorów tła w zależności od trybu pracy.`  
   -> **[Jak]** (wytyczne dotyczące stylistyki i techniki wykonania wizualnego)

9. `Przycisk Start ma uruchamiać odliczanie sekunda po sekundzie, Pauza wstrzymywać odliczanie, a Reset przywracać pełny czas bieżącego trybu.`  
   -> **[Po czym poznać, że skończone]** (kryterium poprawnego działania i zachowania elementów sterujących)

10. `Gdy zegar osiągnie 00:00, aplikacja ma bezbłędnie zainkrementować licznik cykli i samoczynnie przejść do kolejnego właściwego interwału.`  
    -> **[Po czym poznać, że skończone]** (kryterium akceptacji automatycznej zmiany stanów automatu skończonego)

### Statystyka składowych promptu
- **Co ma powstać:** 5
- **Jak:** 3
- **Po czym poznać, że skończone:** 2

**Wniosek:** Najmniej w analizowanym prompcie jest instrukcji z kategorii „po czym poznać, że skończone” (kryteriów akceptacji i weryfikacji), co jest powszechnym zjawiskiem w promptach i sprawia, że to model sztucznej inteligencji musi samodzielnie dopowiadać zachowania brzegowe oraz nieoczywiste stany aplikacji.


---

## Pytanie projektowe: Reset w środku przerwy a licznik cykli

### Pytanie
> **Co ma się stać z licznikiem cykli, kiedy naciśniesz reset w środku przerwy?**

Pytania tego nie da się rozstrzygnąć samym uruchomieniem programu, ponieważ uruchomienie pokazuje jedynie stan faktyczny (jak kod zachowuje się w tej chwili), a nie to, jak zachować się *powinien* według intencji użytkownika czy reguł metodyki.

### Co program robi dzisiaj?
W obecnej wersji programu, gdy naciśniesz przycisk **Reset** w trakcie trwania przerwy (krótkiej lub długiej):
1. Odliczanie zostaje zatrzymane (`isRunning = false`).
2. Czas na wyświetlaczu zostaje przywrócony do pełnego czasu trwania danej przerwy (do `05:00` w krótkiej przerwie lub `15:00` w długiej przerwie).
3. **Licznik ukończonych cykli pozostaje nienaruszony** – zachowuje swoją dotychczasową wartość (np. po 2 ukończonych blokach pracy nadal wyświetla cykl 2).
4. Aplikacja nadal pozostaje w trybie przerwy – nie przeskakuje samowolnie do trybu pracy.

### Czyja to decyzja — moja czy modelu?
**Jest to decyzja modelu sztucznej inteligencji.**

W prompcie pokazowym autor nie zawarł żadnej wytycznej regulującej przypadek brzegowy resetowania minutnika poza trybem pracy. Prompt zawierał jedynie lakoniczne sformułowanie: *„Reset przywracać pełny czas bieżącego trybu”*. 

Model generujący kod musiał podjąć autonomiczną decyzję architektoniczną:
- Zinterpretował słowo „bieżący tryb” ściśle lokalnie (`mode === 'shortBreak' ? 5*60 : ...`).
- Nie powiązał akcji resetu w trybie przerwy z modyfikacją zmiennej globalnej `completedCycles`.

Z punktu widzenia ergonomii pracy decyzja modelu okazała się sensowna – zapobiega przypadkowej utracie zarejestrowanych 25-minutowych bloków skupienia tylko dlatego, że ktoś chciał od nowa zalać herbatę i zresetować stoper przerwy. Niemniej jednak fakt, że zachowanie to nie zostało świadomie zdefiniowane przez człowieka przed wygenerowaniem kodu, jest dowodem na to, jak brak kryteriów akceptacji w prompcie przenosi decyzje projektowe na model AI.
