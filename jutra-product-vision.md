# jutra: Wirtualny sobowtór przyszłego „ja”

## 1. Wizja i cel projektu

**jutra** to aplikacja wspierająca rozwój nastolatków poprzez umożliwienie im dialogu z wirtualną wersją samych siebie z przyszłości (w perspektywie **+5, +10, +20 i +30 lat**). Projekt opiera się na koncepcji **ciągłości przyszłego ja (Future Self-Continuity)**. Badania psychologiczne wykazują, że silniejsza więź z własną przyszłą wersją redukuje skłonność do natychmiastowej gratyfikacji, poprawia planowanie finansowe i wspiera zdrowsze wybory życiowe.

---

## 2. Fundamenty naukowe persony

Persona agenta w aplikacji jutra nie jest statycznym opisem, lecz **dynamicznie obliczanym stanem psychologicznym**:

- **Zasada dojrzałości (Maturity Principle):** logika agenta implementuje naukowe trendy starzenia się osobowości. Z każdą dekadą agentowi algorytmicznie podnoszone są parametry Sumienności i Ugodowości, a obniżany poziom Neurotyczności.
- **Stadia Eriksona:** każdy sub-agent (np. „Ja za 20 lat”) operuje w ramach specyficznego kryzysu psychospołecznego. Wersja **+10 lat** (ok. 25 r.ż.) skupia się na budowaniu bliskości (*Intymność vs. izolacja*), a wersja **+30 lat** na mentoringu i wpływie społecznym (*Generatywność vs. stagnacja*).
- **Model RIASEC:** system mapuje obecne hobby i zainteresowania użytkownika na trajektorie zawodowe (np. zainteresowania badawcze u nastolatka przekładają się na mądrość ekspercką u dojrzałego sobowtóra).
- **Framework PB&J (Psychology of Behavior and Judgments):** agent generuje psychologiczne uzasadnienia dla swoich „przyszłych” decyzji, aby uniknąć generycznych odpowiedzi i brzmieć jak autentyczna, dojrzała wersja użytkownika.

---

## 3. Architektura logiczna agentów

### A. Koordynacja (Multi-Agent Orchestration)

System wykorzystuje strukturę hierarchiczną:

- **Agent główny (orkiestrator):** zarządza intencją rozmowy i deleguje głos do odpowiedniego „wcielenia czasowego”.
- **Agenty specjalistyczne (wcielenia):** każdy posiada instrukcje systemowe kalibrujące ton, słownictwo i priorytety zgodnie z wiekiem i profilem psychometrycznym użytkownika.

### B. Rurociąg tożsamości (Ingestion Pipeline)

Budowa persony odbywa się poprzez analizę cyfrowego śladu użytkownika:

- **Moduł ekstrakcji:** przetwarza dane wejściowe (np. posty z mediów społecznościowych, opisy zainteresowań) w celu identyfikacji stałych wartości, przekonań i cech charakteru.
- **Profilowanie psychometryczne:** mapuje surowe dane na profil **Wielkiej Piątki (OCEAN)**, który stanowi bazę do dalszej symulacji starzenia.

### C. Mechanizm ID-RAG (Identity-RAG)

Zamiast standardowego wyszukiwania semantycznego, system stosuje **ID-RAG**, uziemiając agenta w **grafie wiedzy o tożsamości**:

- Przechowuje on relacje (np. `Użytkownik → ceni → niezależność`).
- Gwarantuje, że sobowtór za 30 lat zachowuje ten sam **rdzeń wartości** co nastolatek, mimo ewolucji stylu komunikacji.

---

## 4. Zarządzanie pamięcią i kontekstem

Aplikacja implementuje warstwową strukturę pamięci:

- **Pamięć sesyjna:** zarządza bieżącą wymianą zdań i stanem rozmowy.
- **Trwały Bank Pamięci:** po każdej sesji agent wyodrębnia kluczowe fakty i preferencje (np. „użytkownik boi się porażki”), które są utrwalane i automatycznie wstrzykiwane do instrukcji systemowej przy kolejnych logowaniach.

---

## 5. Bezpieczeństwo i etyka

- **Ekranowanie (Input / Output Shielding):** system skanuje wejścia i wyjścia pod kątem treści nieodpowiednich dla niepełnoletnich, toksyczności oraz prób manipulacji agentem.
- **Wykrywanie kryzysów:** mechanizm „czerwonych flag” przerywa symulację i podaje informacje pomocowe, jeśli wykryje u użytkownika sygnały silnego kryzysu psychicznego.
- **Transparentność:** zgodnie z wymogami prawnymi (np. **EU AI Act**), każda interakcja jest wyraźnie oznaczona jako wygenerowana przez AI.

---

## Wytyczne dla logiki kodu

- Wartości cech osobowości (**OCEAN**) muszą być normalizowane do jednostek populacyjnych (np. **T-score**).
- Przy implementacji zmiany wieku należy stosować **regresję liniową cech osobowości** (np. wzrost sumienności o ok. **0.15 odchylenia standardowego na każdą dekadę**).
- **Graf tożsamości** musi priorytetyzować węzły dotyczące **wartości (Values)** nad ulotnymi preferencjami.
