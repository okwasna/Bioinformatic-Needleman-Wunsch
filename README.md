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

needleman_wunsch(seq1, seq2, match_score, mismatch_penalty, gap_penalty)
Wykonuje algorytm wyrównania Needleman-Wunsch na dwóch sekwencjach (seq1 i seq2). Parametry match_score, mismatch_penalty i gap_penalty pozwalają dostosować punktację za zgodności, niezgodności i przerwy odpowiednio.

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
