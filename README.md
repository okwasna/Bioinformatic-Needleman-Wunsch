# Bioinformatic-Needleman-Wunsch
Narzędzie do Wyrównywania Sekwencji

To narzędzie jest zaprojektowane do wyrównywania dwóch sekwencji biologicznych przy użyciu algorytmu Needleman-Wunsch. Zaimplementowano je w Pythonie i jest przeznaczone do uruchamiania w środowisku Jupyter. Skrypt odczytuje dane sekwencji z pliku FASTA, wyrównuje sekwencje i eksportuje wynik do pliku tekstowego.

Wymagania

Python w wersji 3.10 lub nowszej
Biopython w wersji 1.81 lub nowszej
Przed uruchomieniem narzędzia upewnij się, że zainstalowałeś wymagany pakiet Pythona: pip install biopython

Użycie

Aby użyć tego narzędzia, wykonaj następujące kroki:

Umieść swój plik FASTA zawierający dokładnie dwie sekwencje w tym samym katalogu co skrypt.
Uruchom skrypt w środowisku Jupyter. Zostanie wyświetlone monit o przesłanie pliku FASTA.
Skrypt przetworzy sekwencje i zapisze wynik wyrównania do pliku tekstowego.

Funkcje

Algorytm Needleman-Wunsch jest metodą używaną do globalnego wyrównywania sekwencji, co oznacza, że znajduje optymalne dopasowanie całych sekwencji od początku do końca. 

Funkcja needleman_wunsch implementuje algorytm Needleman-Wunsch i przyjmuje dwa łańcuchy znaków (seq1, seq2) reprezentujące sekwencje do wyrównania oraz trzy wartości numeryczne: match_score, mismatch_penalty, i gap_penalty reprezentujące odpowiednio: punktację za zgodność, karę za niezgodność i karę za przerwę (gap).

Oto szczegółowy opis działania tej funkcji:

Inicjalizacja macierzy skorowania (score_matrix): Tworzy macierz o wymiarach (m+1) x (n+1), gdzie m to długość seq1, a n to długość seq2. Każda komórka w macierzy odpowiada skumulowanej punktacji za dopasowanie lub wprowadzenie przerw do danego momentu w sekwencjach.
Inicjalizacja macierzy wskazań kierunków (traceback_matrix): Tworzy drugą macierz, która jest używana do zapisywania, skąd przyszła dana punktacja w score_matrix. Dzięki niej będziemy w stanie odtworzyć optymalne dopasowanie po zakończeniu wypełniania score_matrix.
Wypełnienie pierwszego wiersza i kolumny: Ustawia punktację w pierwszym wierszu i kolumnie zgodnie z karami za przerwę, zakładając, że każda przerwa w jednej z sekwencji ma stałą karę.

Wypełnianie macierzy skorowania i traceback: Dla każdej komórki w macierzy oblicza maksymalną punktację z możliwych ruchów:
diag - punktacja za zgodność (lub niezgodność) znaków w obu sekwencjach,
up - punktacja za wprowadzenie przerwy w pierwszej sekwencji,
left - punktacja za wprowadzenie przerwy w drugiej sekwencji.

Ruch, który daje najwyższą punktację, jest zapisywany w traceback_matrix.

Śledzenie wsteczne: Rozpoczynając od dolnego prawego rogu traceback_matrix, funkcja odtwarza optymalne dopasowanie. Jeśli ruch przyszedł na przekątnej, to znaki są dopasowane do siebie. Jeśli przyszedł z góry, to w pierwszej sekwencji wprowadzana jest przerwa. Jeśli przyszedł z lewej, to przerwa wprowadzana jest w drugiej sekwencji. Ten proces jest kontynuowany aż do osiągnięcia górnego lewego rogu macierzy.

read_fasta(file_path)
Odczytuje plik FASTA z podanej file_path i zwraca listę sekwencji.

main(fasta_file)
Główna funkcja, która koordynuje odczytywanie pliku FASTA, wyrównywanie sekwencji i zapisywanie wyników do alignment_result.txt.

Wynik

Skrypt wygeneruje plik o nazwie alignment_result.txt, który zawiera wyrównane sekwencje.




Przykład uruchomienia skryptu w komórce Jupyter:

fasta_file = "ścieżka_do_twojego_pliku.fasta"
print(main(fasta_file))

W rezultacie otrzymasz:


Wynik dopasowania został zapisany do alignment_result.txt


Uwaga

Skrypt jest zaprojektowany do użycia w środowisku Jupyter z integracją Google Colab do przesyłania plików.
Jeśli używasz innego środowiska lub chcesz zautomatyzować proces wprowadzania danych, możesz potrzebować dostosować sekcje wejścia/wyjścia plików odpowiednio.
