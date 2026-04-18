# Architektura Chrono-Self: Autonomiczne Agenty Google ADK i Rurociągi Tożsamości w Modelowaniu Przyszłego „Ja”

Projekt **Chrono-Self** to zaawansowany ekosystem agentowy zbudowany w oparciu o **Google Agent Development Kit (ADK)**, który transformuje surowe dane o użytkowniku w logicznie spójnego, ewoluującego w czasie „cyfrowego sobowtóra”. System nie tylko generuje odpowiedzi, ale rozumuje w oparciu o strukturalny model tożsamości, zasilany przez rurociągi danych z mediów społecznościowych i uziemiony w paradygmatach psychologii rozwojowej.

---

## 1. Architektura systemu: Multi-Agent Orchestration (ADK)

Sercem systemu jest hierarchiczna struktura agentów zdefiniowana w ADK, wykorzystująca wzorzec **Coordinator / Dispatcher**.

### Root Agent (globalny koordynator)

Pełni rolę „Air Traffic Control”. Analizuje intencje użytkownika i zarządza przepływem rozmowy, delegując zadania do specjalistycznych sub-agentów.

### Persona Specialist Agents (perspektywy czasowe)

Zestaw sub-agentów (np. `FutureSelf_10`, `FutureSelf_30`), z których każdy posiada unikalne instrukcje systemowe modyfikujące profil bazowy użytkownika o parametry wynikające z wieku i stadium rozwoju.

### Identity Extraction Agent

Autonomiczny agent działający w tle, którego zadaniem jest destylacja cech osobowości z surowych danych wejściowych.

---

## 2. Pętla tożsamości: od surowych danych do persony

Logika budowy persony opiera się na hybrydowym podejściu: połączeniu **Cold Start** (kwestionariusz) z dynamicznym uczeniem się (**Ingestion Pipeline**).

### Ingestion Pipeline (rurociąg danych)

Zamiast polegać wyłącznie na deklaracjach użytkownika, system wykorzystuje Vertex AI Search / Agent Builder do ingestii danych z mediów społecznościowych (posty, komentarze, aktywność).

- **Connectors:** wykorzystanie standardowych i niestandardowych konektorów do pobierania danych (np. API Slack, Jira lub scraping mediów społecznościowych do Cloud Storage).
- **Sequential Processing:** `SequentialAgent` analizuje pobrane dane w potoku: **Parser** (oczyszczanie tekstu) → **Extractor** (identyfikacja faktów) → **Psychometrist** (mapowanie na profil OCEAN).

### Mechanizm ID-RAG (Identity Retrieval-Augmented Generation)

W przeciwieństwie do klasycznego RAG, który szuka podobieństwa semantycznego, **ID-RAG** odwołuje się do strukturalnego modelu tożsamości — tzw. **Kroniki (Chronicle)**.

- **Graf tożsamości:** dynamiczny graf wiedzy przechowujący przekonania, wartości i stałe cechy charakteru (np. Użytkownik $\xrightarrow{\text{ceni}}$ lojalność).
- **Grounding:** przy każdej odpowiedzi agent pobiera z grafu „triplety tożsamości”, co gwarantuje, że sobowtór za 30 lat zachowa ten sam rdzeń wartości co 15-latek, mimo zmiany tonu wypowiedzi.

---

## 3. Logika rozumowania i ewolucji persony

Persona agenta jest budowana w oparciu o trzy filary naukowe implementowane bezpośrednio w logice agentów ADK.

### Filar I: Wielka Piątka (OCEAN) i zasada dojrzałości

Profil bazowy (OCEAN) jest pozyskiwany z Ingestion Pipeline (analiza językowa) lub krótkiego kwestionariusza BFI-2. Logika agenta aplikuje do tego profilu **Zasadę Dojrzałości (Maturity Principle)**:

- **Algorytmiczne przesunięcie:** dla agenta `FutureSelf_20` parametry Sumienności i Ugodowości są podnoszone o znormalizowany współczynnik $T$-score, podczas gdy Neurotyczność jest obniżana.
- **Stabilność ipsatywna:** ADK pilnuje, aby relatywny profil cech pozostał stały — jeśli użytkownik jest bardziej kreatywny od 90% rówieśników, jego sobowtór również taki pozostanie w swojej grupie wiekowej.

### Filar II: Stadia Eriksona i RIASEC

Narracja agenta jest osadzona w kryzysach psychospołecznych Erika Eriksona i zainteresowaniach zawodowych RIASEC.

- **Strategia konwersacyjna:** agent `FutureSelf_10` (stadium intymności) priorytetyzuje tematy budowania relacji, podczas gdy `FutureSelf_30` (stadium generatywności) skupia się na mentoringu i wkładzie w społeczeństwo.
- **Vocational modeling:** zainteresowania wykryte u nastolatka są ekstrapolowane na role zawodowe. Przykładowo, pasja do gier i matematyki (RIASEC: Investigative / Realistic) jest przekuwana w narrację o karierze inżyniera oprogramowania.

### Filar III: Framework PB&J (Psychology of Behavior and Judgments)

Aby sobowtór był przekonujący, musi umieć racjonalizować swoje wybory.

- **Psychological scaffolds:** agent wykorzystuje model LLM do generowania uzasadnień: „Dlaczego osoba o Twoich cechach podjęłaby taką decyzję w przyszłości?”. Dzięki temu odpowiedzi nie są generyczne, lecz wynikają z głębokiego zrozumienia psychologii użytkownika.

---

## 4. Zarządzanie pamięcią i kontekstem w Google Cloud

System wykorzystuje wielowarstwową pamięć zarządzaną przez Vertex AI Agent Engine:

- **Sessions (pamięć krótkoterminowa):** przechowuje bieżący stan rozmowy i kontekst ostatnio zadanych pytań.
- **Memory Bank (pamięć długoterminowa):** tutaj `save_session_to_memory_callback` utrwala wyekstrahowane fakty i preferencje (np. „użytkownik boi się porażki”), które są automatycznie wstrzykiwane do instrukcji systemowej przy kolejnych logowaniach.

---

## 5. Bezpieczeństwo: Model Armor

W interakcji z nastolatkami kluczowe jest wdrożenie bariery **Model Armor**:

- **Input / Output Shielding:** skanowanie promptów i odpowiedzi w czasie rzeczywistym pod kątem toksyczności, prób manipulacji (jailbreaking) oraz wycieku danych PII.
- **Czerwone flagi:** integracja z systemami wykrywania kryzysów psychicznych — w przypadku wykrycia treści niebezpiecznych agent przerywa symulację i podaje kontakt do linii wsparcia.

---

## Podsumowanie techniczne (hackathon)

Implementacja w **Google ADK** pozwala na stworzenie agenta, który nie symuluje, lecz **oblicza** przyszłe ja. Połączenie potoku danych z mediów społecznościowych, grafu tożsamości ID-RAG oraz naukowo skalibrowanych parametrów OCEAN sprawia, że Chrono-Self staje się wiarygodnym, cyfrowym mentorem, który rośnie i dojrzewa matematycznie wraz z użytkownikiem.
