# microLogger Prosty Logger Krótkofalarski & Wsparcie Akcji Dyplomowych

## O Projekcie

Ten projekt to minimalistyczny logger krótkofalarski, stworzony z myślą o prostocie i szybkości logowania łączności (QSO). Dodatkowo, oferuje funkcje wspomagające organizację i uczestnictwo w akcjach dyplomowych, działając jako darmowa i otwarta alternatywa dla komercyjnych rozwiązań.

## Motywacja

Nie każdy krótkofalowiec potrzebuje zaawansowanego loggera z rozbudowanymi funkcjami i integracjami. Dla wielu wystarczające jest proste zanotowanie łączności, często bezpośrednio na platformach takich jak QRZ.com. Jednak podczas akcji dyplomowych lub ekspedycji, gdzie liczy się szybkość i precyzja, ręczne wpisywanie danych na stronę internetową staje się uciążliwe i niepraktyczne.

Pierwotnie powstał prosty program do szybkiego logowania QSO i generowania pliku ADIF. Po jego ukończeniu podjęto decyzję o rozszerzeniu funkcjonalności i stworzeniu darmowej, otwartej usługi, podobnej do HamAward.cloud, która będzie wspierać społeczność krótkofalowców.

## Cechy

* **Minimalistyczny Logger:** Szybkie wprowadzanie danych QSO (znak, raporty).
* **Generowanie ADIF:** Automatyczny zapis łączności do lokalnego pliku w standardowym formacie ADIF, gotowego do wysłania do dowolnego serwisu (np. LoTW, eQSL, QRZ.com).
* **Komunikacja Sieciowa (Klient):**
    * Wysyłanie danych STATUS i LOGGED w standardzie kompatybilnym z popularnymi programami (np. JTDX).
    * Przesyłanie surowego rekordu ADIF każdej zalogowanej łączności przez UDP na wskazany adres serwera.
* **Wsparcie Serwerowe (dla Akcji Dyplomowych):**
    * Odbiór i przetwarzanie ADIF przesłanego przez logger.
    * Zapis QSO do bazy danych serwera, jeśli operator uczestniczy w skonfigurowanej akcji dyplomowej.
    * Logowanie połączeń od operatorów spoza akcji (wraz z IP/portem).
    * Wyświetlanie aktywnych operatorów (uczestniczących w akcji) na stronie serwera wraz z częstotliwością ostatniej łączności przez określony czas.
* **Darmowy i Otwarty:** Projekt rozwijany na zasadach Open Source.

## Jak To Działa

**Część Kliencka (Logger):**

1.  Operator wprowadza znak stacji i raporty.
2.  Naciśnięcie klawisza Enter zatwierdza łączność.
3.  QSO jest natychmiast zapisywane do lokalnego pliku ADIF.
4.  Program jednocześnie wysyła przez sieć (UDP) dane STATUS i LOGGED (w formacie JTDX) oraz surowy rekord ADIF tej łączności na adres serwera skonfigurowany przez operatora.

**Część Serwerowa (Opcjonalna - dla Akcji Dyplomowych):**

1.  Serwer nasłuchuje na skonfigurowanym porcie UDP.
2.  Po odebraniu danych, serwer weryfikuje i czyści rekord ADIF.
3.  Jeśli operator (na podstawie znaku z ADIF) uczestniczy w akcji dyplomowej hostowanej przez serwer, QSO jest zapisywane w bazie danych tej akcji.
4.  Łączności od operatorów nieuczestniczących w akcji są logowane (np. do celów diagnostycznych).
5.  Aktywni operatorzy biorący udział w akcji są wyświetlani na dedykowanej stronie serwera przez czas określony w konfiguracji, informując o ich ostatniej częstotliwości pracy.

## Podsumowanie

Logger może działać w pełni lokalnie jako szybkie i proste narzędzie do tworzenia plików ADIF, lub być wykorzystywany w połączeniu z serwerem, stanowiąc cenne wsparcie podczas akcji dyplomowych, umożliwiając podgląd postępów w czasie rzeczywistym.
