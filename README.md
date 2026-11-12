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
