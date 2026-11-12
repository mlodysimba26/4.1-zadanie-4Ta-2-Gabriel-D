# Specyfikacja techniczna minutnika: Co miał robić

## Co spisujesz dzisiaj
- **Nazwa projektu:** Minutnik Pomodoro (specyfikacja spisana po fakcie z uruchomionej aplikacji).
- **Cel spisywania:** Inżynieria wsteczna i odtworzenie specyfikacji wymagań na podstawie bezpośredniej interakcji z uruchomionym programem, bez zaglądania do materiałów lekcyjnych i założeń wstępnych.
- **Przedmiot opisu:** Aplikacja minutnika czasu pracy i przerw w technice Pomodoro.

---

## 1. Co robi
- Odlicza czas sesji pracy wynoszący 25 minut (1500 sekund).
- Po upływie czasu pracy automatycznie zwiększa licznik ukończonych cykli pracy.
- Po zakończeniu czasu pracy przełącza się w tryb krótkiej przerwy wynoszący 5 minut (300 sekund).
- Po ukończeniu każdego czwartego cyklu pracy (4, 8 itd.) przełącza się w tryb długiej przerwy wynoszącej 15 minut (900 sekund).
- Wyświetla czas w czytelnym formacie cyfrowym `MM:SS` oraz aktualizuje tytuł karty w przeglądarce.
- Wyświetla aktualny tryb pracy: „Praca (Skupienie)”, „Krótka przerwa (5 min)” lub „Długa przerwa (15 min)”.
- Zmienia kolorystykę interfejsu (tło i akcenty) w zależności od aktywnego trybu (czerwony dla pracy, zielony dla krótkiej przerwy, niebieski dla długiej przerwy).
- Zapewnia wizualizację postępu cyklu w postaci 4 punktów wskaźnika.
- Umożliwia sterowanie stanem za pomocą trzech przycisków:
  - **Start:** uruchamia odliczanie co sekundę.
  - **Pauza:** wstrzymuje odliczanie w dowolnym momencie.
  - **Reset:** przywraca czas początkowy dla bieżącego trybu i zatrzymuje zegar.

---

## 2. Czego nie robi
- Nie pozwala użytkownikowi na zmianę lub personalizację długości czasów pracy i przerw z poziomu interfejsu (wartości są zakodowane na stałe).
- Nie zapisuje stanu odliczania ani liczby ukończonych cykli w pamięci trwałej (np. `localStorage`), przez co odświeżenie lub zamknięcie strony kasuje cały postęp.
- Nie odtwarza dźwięku ani powiadomienia dźwiękowego w momencie ukończenia odliczania (informacja jest wyłącznie wizualna).
- Nie wysyła systemowych powiadomień przeglądarkowych (Web Notifications API), gdy karta jest nieaktywna w tle.
- Nie zawiera formularza zadań ani listy to-do (ang. *backlog / distraction list*), która pozwalałaby wpisywać zadania realizowane w danym cyklu.
- Nie posiada przycisku bezpośredniego pominięcia przerwy lub natychmiastowego przejścia do następnego cyklu.
- Nie prowadzi historii statystyk produktywności (dziennych, tygodniowych wykresów).

---

## 3. Pięć zdań „Kiedy …, to …”
1. **Kiedy** naciśniesz przycisk „Start”, **to** minutnik rozpoczyna odliczanie czasu w dół sekunda po sekundzie.
2. **Kiedy** naciśniesz przycisk „Pauza”, **to** odliczanie czasu zostaje natychmiast zatrzymane, zachowując aktualną liczbę sekund na wyświetlaczu.
3. **Kiedy** czas trwania sesji pracy osiągnie wartość 00:00, **to** aplikacja zwiększa licznik ukończonych cykli o jeden, zmienia kolor tła na zielony i przechodzi do odliczania 5 minut krótkiej przerwy.
4. **Kiedy** licznik ukończonych cykli pracy osiągnie 4, **to** minutnik po zakończeniu sesji skupienia uruchamia długą przerwę (15 minut) z niebieskim motywem zamiast przerwy 5-minutowej.
5. **Kiedy** naciśniesz przycisk „Reset” w trakcie trwania pracy, **to** wyświetlacz powraca do wartości 25:00, a licznik czasu zatrzymuje się.

---

## 4. Do ustalenia
- **Zachowanie licznika cykli przy resecie w przerwie:** Co dokładnie powinno się stać z licznikiem ukończonych cykli, gdy użytkownik naciśnie „Reset” w trakcie trwania przerwy – czy zerujemy całą serię, czy tylko czas bieżącego odpoczynku?
- **Automatyczny vs ręczny start sesji pracy:** Czy po zakończeniu przerwy minutnik powinien bezwarunkowo ruszać z kolejnym 25-minutowym cyklem pracy, czy czekać na gotowość użytkownika i kliknięcie „Start”?
- **Trwałość sesji:** Czy po przypadkowym zamknięciu lub odświeżeniu karty aplikacja powinna wznawiać odliczanie z `localStorage`?
- **Sygnalizacja dźwiękowa:** Jaki rodzaj dźwięku i o jakiej głośności ma informować o końcu cyklu przy zminimalizowanej przeglądarce?
- **Możliwość pominięcia przerwy:** Czy należy dodać przycisk „Pomiń przerwę”, gdy użytkownik chce pracować dalej bez czekania?
