# Big Data i Analiza Danych - Kompletne Notatki

## 1. Fundamenty Big Data

### Definicje i Koncepcje Podstawowe

**Big Data** to nie tylko duże zbiory danych, ale zjawisko, które fundamentalnie zmienia sposób
podejmowania decyzji. Dane charakteryzują się różnorodnością, są trudne do przetworzenia
tradycyjnymi metodami, ale jednocześnie są bardzo wartościowe. Termin spopularyzowany około 5 lat
temu.

### Model 5 V - Charakterystyka Big Data

1. **Volume (Objętość)**
    Ogromne ilości danych w skali petabajtów (PB) i eksabajtów (EB)
    Znacznie przekracza możliwości tradycyjnych systemów
2. **Velocity (Prędkość)**
    Szybki przepływ danych i potrzeba analizy w czasie rzeczywistym
    Kluczowe technologie: Apache Kafka, Apache Flink
    Wymagania dotyczące natychmiastowego przetwarzania
3. **Variety (Różnorodność)**
    Dane ustrukturyzowane: tabele SQL, bazy relacyjne
    Dane nieustrukturyzowane: teksty, obrazy, wideo, logi, media społecznościowe
4. **Veracity (Wiarygodność)**
    Dane mogą być niekompletne, błędne lub niespójne
    Wymagana walidacja, filtrowanie i czyszczenie danych
    Zarządzanie jakością i wiarygodnością źródeł
5. **Value (Wartość)**
    Korzyści biznesowe z analizy danych
    Lepsze zrozumienie klienta, optymalizacja procesów
    Przekształcanie surowych danych w wartościowe insights

### Tradycyjna Analiza vs. Big Data - Porównanie

```
Aspekt Tradycyjna Analiza Big Data
Objętość Danych Megabajty (MB) Petabajty (PB), Eksabajty (EB)
Struktura
Danych Ustrukturyzowane^ (tabele^ SQL) Ustrukturyzowane^ +^ nieustrukturyzowane
```

```
Aspekt Tradycyjna Analiza Big Data
Prędkość
Analizy Okresowa^ (miesięczne^ raporty) Czas^ rzeczywisty
Narzędzia Excel, SQL, RQS Hadoop, Spark, Flink
Cel Analizy Opis przeszłości (ile sprzedano?) Psprzrogenozowdaż?)anie^ przyszłości^ (dlaczego^ spadła
```
```
Rola Człowieka Cprzentretwalnarza^ a(wynieb)ór^ danych, Wspomagana przez AI (wzorce, anomalie)
Jakość Danych Ujednolicona, z jednego źródła Różnorodna, błędy, duplikaty
Infrastruktura Serwery indywidualne Chmura, systemy rozproszone
```
### Kluczowe Koncepcje

```
Data Lake : Centralne repozytorium przechowujące dane w surowym formacie
Dark Data : Dane rzadko odczytywane, przechowywane ze względów prawnych i compliance
Schema on Read : Struktura danych definiowana dopiero przy odczycie (np. Apache Hive)
```
## 2. Systemy Baz Danych i Przechowywania

### Bazy Relacyjne (SQL)

```
Przykłady : SQL Server, MySQL, PostgreSQL
Charakterystyka : Tabele połączone kluczami, ACID properties
Zastosowanie : Transakcje finansowe, systemy ERP
```
### Bazy Nierelacyjne (NoSQL)

```
MongoDB : Baza dokumentowa używająca BSON (binary JSON)
Bazy grafowe : Neo 4 j - optymalizowane do przechowywania relacji
Bazy kolumnowe : HBase - inspirowane BigTable od Google
```
### Rozproszone Systemy Plików

**Hadoop Distributed File System (HDFS)**

```
Dzielenie dużych plików na mniejsze bloki (domyślnie 64 KB)
Replikacja bloków na wielu węzłach (data nodes) dla redundancji
Zapewnienie dostępności danych przy awariach węzłów
```
**Google File System (GFS)**

```
System plików Google oparty na MapReduce
```

```
Podstawa dla wielu rozwiązań Big Data
```
**Amazon S 3**

```
System przechowywania obiektów w chmurze
Dane replikowane w co najmniej 3 lokalizacjach
Wysoka dostępność i trwałość danych
```
## 3. Narzędzia i Technologie Big Data

### Ekosystem Hadoop

**Hadoop Core**

```
HDFS : Rozproszony system plików
MapReduce : Framework do przetwarzania danych
YARN : Resource Manager dla zarządzania zasobami klastra
```
**Narzędzia Hadoop**

```
Apache Hive : SQL na danych Hadoop, tłumaczenie zapytań na zadania MapReduce
Apache Pig : Uproszczenie zapytań w Hadoop, język skryptowy
HBase : Baza kolumnowa, szybki dostęp do danych NoSQL
```
### Apache Spark - Zaawansowane Przetwarzanie

**Architektura Spark**

```
RDD (Resilient Distributed Dataset) :
Przechowywanie danych w pamięci RAM dla szybszego dostępu
Lazy transformation - transformacje wykonywane dopiero przy akcji
Niemutowalna, rozproszona kolekcja danych
Podstawowa abstrakcja w Sparku
DataFrame :
Struktury danych do analizy, zorganizowane w kolumny
Oferuje optymalizacje wydajności i schemat
Umożliwia operacje SQL na danych
Dataset :
Połączenie RDD i DataFrame
Silne typowanie i optymalizacja
Brak natywnego wsparcia w PySpark
```

```
Typowane kolekcje danych
```
**Komponenty Spark**

```
Spark SQL : Zapytania SQL na danych w Sparku
Spark Streaming : Przetwarzanie strumieniowe danych
MLlib : Biblioteka uczenia maszynowego
GraphX : Biblioteka do przetwarzania grafów
```
**Spark vs MapReduce**

```
Spark : Szybszy, przetwarzanie w pamięci RAM, lazy evaluation
MapReduce : Wolniejszy, zapis na dysk po każdej operacji
Zastosowania Spark : Iteracyjne algorytmy ML, interactive analytics
```
### Inne Kluczowe Technologie

```
Apache Kafka : System transportu wiadomości w czasie rzeczywistym, kolejka komunikatów
Apache Flink : Przetwarzanie strumieniowe o niskich opóźnieniach
MongoDB : Baza dokumentowa, format BSON, elastyczny schemat
Neo 4 j : Popularna baza grafowa z językiem Cypher
```
## 4. Architektury Systemów Rozproszonych

### Wzorce Architektoniczne

**Master-Worker**

```
Master : Zarządza kolejką zadań, koordynuje pracę
Worker : Pobiera zadania z kolejki i je wykonuje
Zalety : Centralna kontrola, łatwe zarządzanie
Wady : Single point of failure
```
**Peer-to-Peer (P 2 P)**

```
Wszystkie węzły są równe i wymieniają się danymi
Brak centralnego koordynatora
Zalety : Odporność na awarie, skalowalność
Wady : Złożoność synchronizacji
```
**MapReduce**

```
Map : Dzielenie danych na pary klucz-wartość
```

```
Reduce : Grupowanie i agregacja według klucza
Zastosowanie : Przetwarzanie dużych zbiorów danych
```
### Hadoop 2.0 Architecture

### Zaawansowane Wzorce

**CQRS (Command Query Responsibility Segregation)**

```
Oddzielenie operacji zapisu (commands) i odczytu (queries)
Różne modele danych dla zapisu i odczytu
Optymalizacja wydajności dla konkretnych przypadków użycia
```
**Event Sourcing**

```
Przechowywanie historii zdarzeń zamiast aktualnego stanu
Możliwość odtworzenia stanu w dowolnym momencie
Immutable event store
```
**Saga Pattern**

```
Sekwencja lokalnych transakcji
Akcje kompensacyjne w przypadku błędu
Zapewnienie spójności w systemach rozproszonych
```
**Outbox Pattern**

```
Zapis zdarzenia do specjalnej tabeli w tej samej transakcji co dane biznesowe
Gwarancja publikacji zdarzeń
Rozwiązanie problemu dual write
```
### Architektura Lambda

```
Połączenie warstwy wsadowej (batch) i strumieniowej (stream)
Speed layer dla real-time processing
Batch layer dla historical processing
Serving layer dla zapytań
```
## 5. CAP Theorem - Fundamenty Systemów Rozproszonych

W systemach rozproszonych można zagwarantować tylko **2 z 3 cech** :

```
Klient → Resource Manager → Application Manager (na każdym Node) → Node Manager
```

### Consistency (Spójność)

```
Wszyscy użytkownicy widzą te same dane w tym samym czasie
Wszystkie węzły mają identyczną kopię danych
Przykład : Systemy bankowe, gdzie saldo musi być spójne
```
### Availability (Dostępność)

```
System zawsze odpowiada na zapytania w rozsądnym czasie
Brak downtime, ciągłość działania
Przykład : Serwisy społecznościowe, gdzie dostępność jest kluczowa
```
### Partition Tolerance (Odporność na podział sieci)

```
System działa nawet przy przerwaniu komunikacji między węzłami
Tolerancja awarii sieci
Wymagane w systemach rozproszonych
```
### Kompromisy CAP

```
CP (Consistency + Partition Tolerance) : Systemy bankowe - lepiej być niedostępnym niż
niespójnym
AP (Availability + Partition Tolerance) : Media społecznościowe - lepiej pokazać stare dane niż
być niedostępnym
Eventual Consistency : Dane synchronizują się po pewnym czasie (kompromis)
```
## 6. Przetwarzanie Strumieniowe (Stream Processing)

### Charakterystyka

```
Analiza danych w czasie rzeczywistym, w momencie ich napływu
Cechy kluczowe :
Niskie opóźnienia (low latency)
Ciągłość przetwarzania
Skalowalność pozioma
Stabilność i fault tolerance
```
### Operacje Strumieniowe

```
Filtrowanie : Selekcja relevantnych danych
Transformacje : Przekształcanie formatu danych
Agregacje : Sumowanie, liczenie, średnie w oknach czasowych
```

```
Join : Łączenie strumieni danych
```
### Modele Dostarczania Zdarzeń

```
At Most Once : Może zostać utracone, ale nie duplikowane
At Least Once : Może być duplikowane, ale nie utracone
Exactly Once : Dokładnie raz - najtrudniejsze do osiągnięcia
```
### Apache Spark Structured Streaming

**Koncepcja**

```
Traktuje strumień danych jako nieskończoną tabelę
Wykorzystuje SQL do transformacji danych
Continuous Processing Engine dla przetwarzania ciągłego
```
**Mikro-batche**

```
Spark przetwarza dane w małych partiach generowanych co sekundę
Balans między real-time a batch processing
Optymalizacja dla throughput
```
**Okna Czasowe (Time Windows)**

```
Dane analizowane w oknach czasowych (np. 20 sekund)
Okna przesuwane co określony interwał (np. 5 sekund)
Sliding Windows : Nakładające się okna
Tumbling Windows : Nie nakładające się okna
```
**Watermark**

```
Mechanizm opóźnienia przetwarzania zdarzeń (np. 6 sekund)
Umożliwia uwzględnienie opóźnionych danych
Pomaga radzić sobie z out-of-order events
Balans między latency a completeness
```
## 7. Load Balancing i Tolerancja Błędów

### Load Balancing (Równoważenie Obciążenia)

Równomierne rozdzielanie obciążenia pomiędzy serwery/procesy dla optymalizacji wydajności.

**Algorytmy Load Balancing**

```
Round Robin : Cykliczne przydzielanie zadań
```

```
Least Connections : Zadania do najmniej obciążonego serwera
IP Hash : Routing bazowany na hash IP klienta
Weighted Round Robin : Uwzględnienie wagi/mocy serwerów
Distance Division : Geograficzne rozdzielanie ruchu
```
**Strategie Szczegółowe**

```
Round-Robin : Równomierne rozdzielanie zadań między workerów
List Strategy (Least Loaded) : Przydzielanie do najmniej obciążonego workera
Weight Strategy : Przydzielanie z uwzględnieniem wagi workera (mocniejsze serwery = więcej
zadań)
```
### Tolerancja Błędów (Fault Tolerance)

Zapewnienie ciągłości działania systemu pomimo awarii komponentów.

**Mechanizmy Tolerancji**

```
Replikacja : Duplikowanie danych/usług
Failover : Automatyczne przełączanie na backup
Checkpointing : Zapisywanie stanu systemu
Kompensacja : Akcje cofające skutki błędów
Partycjonowanie : Izolacja awarii
```
**Metryki Monitorowania**

```
Liczba żądań OK vs ERROR
Całkowita liczba żądań
Liczba timeoutów
Liczba powtórzeń (retries)
Latencje : P 95 (95% żądań), P 99 (99% żądań)
```
## 8. Praktyczne Zastosowania - Case Studies

### Wykrywanie Oszustw Bankowych

**Architektura Systemu**

```
Apache Kafka : Zbieranie danych transakcyjnych w real-time
Spark Structured Streaming : Analiza transakcji w mikro-batchach
Reguły biznesowe + Machine Learning : Wykrywanie anomalii
```

**Reguły Wykrywania**

```
Wysokie kwoty : Transakcje przekraczające próg
Duża prędkość : Wiele transakcji w krótkim czasie
Anomalie geograficzne : Transakcje z nietypowych lokalizacji
Wzorce czasowe : Transakcje w nietypowych godzinach
```
**Metryki Jakości**

```
Precision (Precyzja) : TP/(TP+FP) - ile z wykrytych to rzeczywiste oszustwa
Recall (Czułość) : TP/(TP+FN) - ile oszustw udało się wykryć
F1-Score : Harmoniczna średnia precision i recall
False Positives : Błędne alarmy
False Negatives : Przeoczone oszustwa
```
**Automatyzacja Odpowiedzi**

```
Automatyczna blokada podejrzanych transakcji
Powiadomienia SMS do klientów
Eskalacja do zespołów bezpieczeństwa
```
### Analiza Danych z Czujników IoT

**Wykrywanie Anomalii**

```
Brak danych z sensora : Awaria urządzenia
Nieprawidłowe napięcie : Problemy elektryczne
Stosunek mocy do prądu (Amp-rpm) : Anomalie mechaniczne
Parametry telemetryczne : Monitorowanie w oknach czasowych
```
**Przetwarzanie Real-time**

```
Generowanie mikropaków danych co sekundę
Okna czasowe dla agregacji
Watermark dla opóźnionych zdarzeń
Optymalizacja czasu przetwarzania
```
## 9. Bazy Danych Grafowych

### Struktura

```
Węzły (Nodes) : Reprezentują obiekty/entności
```

```
Relacje (Relationships) : Łączą węzły, mają kierunek i właściwości
Właściwości : Atrybuty węzłów i relacji
```
### Standardy i Języki

**RDF (Resource Description Framework)**

```
Standard języka do modelowania zasobów sieciowych
Trójki: Subject-Predicate-Object
SPARQL : Język zapytań do RDF
```
**Neo 4 j i Cypher**

```
Neo 4 j : Najpopularniejsza baza grafowa
Cypher : Deklaratywny język zapytań
Intuicyjna składnia podobna do ASCII art
```
**Gremlin**

```
Język zapytań do różnych baz danych grafowych
Uniwersalny standard dla graph databases
Imperatywny styl programowania
```
### Zastosowania

```
Sieci społecznościowe : Relacje między użytkownikami
Topologie sieci : Infrastruktura IT
Procesy biznesowe : Workflow i zależności
Systemy rekomendacji : Podobieństwa i preferencje
Fraud detection : Analiza podejrzanych wzorców relacji
```
## 10. Formaty Danych i Dokumenty

### JSON (JavaScript Object Notation)

```
Struktura : Pary klucz-wartość
Zastosowanie : Aplikacje internetowe, API, konfiguracje
Zalety : Lekki, czytelny, szeroko wspierany
Wady : Brak schematu, redundancja danych
```
### XML (Extensible Markup Language)

```
Struktura : Hierarchiczna, znaczniki
```

```
Zastosowanie : Systemy zarządzania, wymiana danych B 2 B
Zalety : Walidacja schematu, namespaces, metadata
Wady : Verbose, większy rozmiar
```
### BSON (Binary JSON)

```
Format binarny używany przez MongoDB
Szybsza serializacja/deserializacja
Wsparcie dla dodatkowych typów danych
```
## 11. Symulacje i Demonstracje Praktyczne

### Symulacja Klastrów

Pokazuje **cykl życia klastrów** z następującymi elementami:

**Zdarzenia Klastra**

```
Podziały sieci (Network Partitions) : Izolacja węzłów
Awarie węzłów (Node Failures) : Utrata funkcjonalności
Naprawy (Healing) : Przywracanie łączności
Przyspieszenia/Skoki : Zmiany wydajności
```
**Monitorowane Metryki**

```
Liczba działających węzłów
Liczba zadań w kolejce
Szybkość przetwarzania (TPS - Transactions Per Second)
Status węzłów (Done/Fail)
Partycje (P0, P1) - przynależność węzła
Aktualne zadanie i pasek postępu
```
**Model CP (Consistency + Partition Tolerance)**

```
Tylko większa grupa może zamknąć zadanie
Unika naruszenia spójności kosztem dostępności
Demonstracja kompromisów CAP theorem
```
### Symulacja Load Balancing

**Strategie Testowane**

```
Round-Robin : Cykliczne przydzielanie
```

```
Least-Loaded : Do najmniej obciążonego węzła
Weight-Based : Z uwzględnieniem mocy węzłów
```
**Symulacja Błędów**

```
Awarie losowych węzłów
Automatyczne przekierowanie ruchu
Monitoring czasu recovery
Wpływ na metryki wydajności
```
### Porównanie Wydajności: RDD vs DataFrame vs Dataset

**Tokenizacja Tekstu - Benchmark**

```
RDD : Przetwarzanie krok po kroku, funkcje transformacji
DataFrame : Budowanie kolumn z listami słów, SQL operations
Dataset : Agregacja rekordów do map, strong typing
```
**Wyniki Wydajności**

```
RDD : Elastyczny, ale wolniejszy
DataFrame : Zoptymalizowany, Catalyst optimizer
Dataset : Kompilacja do bytecode, najszybszy
```
## 12. Przetwarzanie w Czasie Rzeczywistym

### Apache Spark Structured Streaming - Szczegóły

**Continuous Processing Engine**

```
Traktowanie strumienia jako nieskończonej tabeli
Incremental processing nowych danych
Trigger modes : Processing time, Once, Continuous
```
**Watermarking Strategy**

```
Event Time : Czas wystąpienia zdarzenia
Processing Time : Czas przetworzenia zdarzenia
Watermark Delay : Tolerancja dla opóźnionych zdarzeń
Late Data Handling : Strategia dla bardzo opóźnionych danych
```
**Output Modes**

```
Append : Tylko nowe rekordy
```

```
Complete : Wszystkie rekordy w każdym batch
Update : Tylko zmienione rekordy
```
### Praktyczna Implementacja

**Kafka + Spark Integration**

```
Kafka Topics : Podział danych na kategorie
Partitioning : Równoległe przetwarzanie
Consumer Groups : Load balancing w Kafka
Offset Management : Tracking postępu przetwarzania
```
**Real-time Analytics Pipeline**

1. **Data Ingestion** : Kafka producers
2. **Stream Processing** : Spark Structured Streaming
3. **Real-time Decisions** : ML models, business rules
4. **Action Triggers** : Alerts, blocking, notifications
5. **Monitoring** : Metrics, dashboards, alerting

## 13. Wzorce Odporności na Błędy

### CQRS + Event Sourcing - Implementacja

**Event Store**

```
Immutable events jako źródło prawdy
Event Types : Created, Updated, Deleted, etc.
Projections : Różne widoki danych z events
Snapshots : Optymalizacja dla długiej historii
```
**Command Side**

```
Walidacja business rules
Generowanie events
Command Handlers : Logika biznesowa
```
**Query Side**

```
Read Models : Zoptymalizowane pod konkretne zapytania
Projections : Budowane z event stream
CQRS Benefits : Niezależna skalowalność read/write
```

### Saga + Outbox - Distributed Transactions

**Saga Execution**

```
Choreography : Każdy serwis wie, co robić dalej
Orchestration : Centralny koordynator
Compensation : Rollback w przypadku błędu
```
**Outbox Implementation**

```
Transactional Outbox : Events w tej samej transakcji co business data
Message Relay : Publikowanie events do message broker
Idempotency : Zagwarantowanie exactly-once processing
```
## 14. Praktyczne Scenariusze i Przypadki Użycia

### Systemy Finansowe

```
Real-time fraud detection
Risk management
Regulatory reporting
Trading systems
```
### E-commerce

```
Recommendation engines
Inventory management
Price optimization
Customer behavior analysis
```
### IoT i Manufacturing

```
Predictive maintenance
Quality control
Supply chain optimization
Energy management
```
### Media i Entertainment

```
Content recommendation
Real-time personalization
Audience analytics
```

```
Content optimization
```
## 15. Najlepsze Praktyki i Wzorce

### Projektowanie Systemów Big Data

1. **Start Small** : Proof of concept przed full-scale
2. **Data Quality First** : Inwestycja w czyszczenie danych
3. **Security by Design** : Szyfrowanie, access control
4. **Monitoring** : Comprehensive metrics i alerting
5. **Cost Optimization** : Right-sizing resources

### Performance Tuning

```
Partitioning Strategy : Optymalne rozdzielenie danych
Caching : In-memory storage dla hot data
Compression : Redukcja I/O i storage costs
Resource Management : CPU, memory, network optimization
```
### Data Governance

```
Data Lineage : Śledzenie pochodzenia danych
Data Catalog : Metadata management
Privacy Compliance : GDPR, CCPA
Retention Policies : Lifecycle management
```
## Słowniczek Kluczowych Terminów

```
Batch Processing : Przetwarzanie danych w dużych porcjach
Stream Processing : Przetwarzanie danych w czasie rzeczywistym
Data Pipeline : Sekwencja operacji przetwarzania danych
ETL/ELT : Extract, Transform, Load / Extract, Load, Transform
Data Warehouse : Centralne repozytorium dla structured data
Data Lake : Repozytorium dla raw data w różnych formatach
OLTP : Online Transaction Processing
OLAP : Online Analytical Processing
Sharding : Poziome partycjonowanie danych
Replication : Duplikowanie danych dla availability
```

**Eventual Consistency** : Spójność osiągana po czasie
**Idempotency** : Operacje bezpieczne do powtarzania


