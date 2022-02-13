# 1. PENDAHULUAN
-----------------------------
PERHATIAN!
 untuk mengakses source code, bisa masuk ke folder src dan cari nama file py sesuai yang sudah saya tuliskan setiap sebelum saya menulis code di file README ini. Contoh:

 _**nama file: `2.1.2.py`**_
```python
>>> the_world_is_flat = True
>>> if the_world_is_flat:
...     print("Be careful not to fall off!")
...     
Be careful not to fall off!
```
--------------------
Selamat datang di pertemuan pertama workshop Python! _First of all_, di sini saya akan membahas beberapa hal tentang bahasa pemrograman Python. Tulisan ini adalah sebuah proses _"Whetting your appetite"_ yang bisa diartikan sebagai "menggugah selera kita untuk memulai belajar menggunakan bahasa pemrograman Python".

Saat kita mengerjakan sesuatu pada komputer, ada kalanya kita harus meng-_automate_ beberapa pekerjaan tersebut. Untuk mengatasi itu, kita bisa menggunakan bahasa pemrograman Python. Python adalah bahasa pemrograman yang sangat mudah digunakan serta menawarkan struktur dan _support_ untuk program berukuran besar. Python juga bisa melakukan proses _error checking_ yang lebih baik daripada C dan memiliki _arrays_ dan _dictionaries_ yang fleksibel.

Python dapat membagi-bagi program menjadi module yang dapat digunakan di program Python yang lain. Python memiliki koleksi _standard modules_ yang sangat banyak yang bisa kita gunakan sebagai basis pada program Python yang kita miliki. Python adalah _interpreted language_, yang artinya kita dapat menghemat waktu saat pengembangan program karena tidak ada proses _compilation_ dan _linking_.

Python membuat penulisan program menjadi padat (_compact_) dan mudah dibaca. Program yang ditulis di Python pada dasarnya memerlukan kode yang lebih sedikit daripada program yang ditulis dengan bahasa C, C++, atau Java karena:
 - Tipe data _high-level_ yang dapat melakukan operasi kompleks dalam satu _statement_.
 - Pengelompokan _statement_ dilakukan dengan _indentation_ (tulisan sedikit menjorok ke kanan), bukan dengan _brackets_.
 - Tidak memerlukan deklarasi variabel atau argumen

<br/>

# 2. MENGGUNAKAN PYTHON INTERPRETER

## 2.1. Memunculkan Interpreter
Biasanya, Python interpreter ter-install pada direktori `/usr/local/bin/python3.10`. Untuk masuk ke direktori tersebut, pada terminal atau shell kita ketik `/usr/local/bin` lalu kita aktifkan interpreter dengan mengetik _command_: `python3.10`. Selain pada direktori tersebut, interpreter juga bisa disimpan di dalam direktori alternatif seperti `/usr/local/python`.

Untuk keluar dari interpreter, kita bisa mengetik `control - D` (pada unix) atau `Control - Z` (pada windows) di _primary prompt_. Jika tidak bisa, kita bisa keluar dari interpreter dengan menggunakan _command_ `quit()`.

Fitur _line-editing_ pada interpreter terdiri dari _interactive editing_, _history subtitution_, dan _code completion_ pada sistem yang mendukung pustaka (_library_) [GNU Readline](https://tiswww.case.edu/php/chet/readline/rltop.html). Untuk memerika apakah _command line editing_ didukung pada interpreter, kita bisa mengetik `Control - P` pada _Python prompt_. Jika berbunyi (_beep_), berarti kita memiliki _command-line editing_. Jika tidak ada apapun yang muncul atau terjadi, berarti _command-line editing_ tidak _available_ dan kita hanya dapat menggunakan _backspace_ untuk menghapus karakter pada suatu baris.

Python interpreter bekerja sama seperti shell Unix. Maksudnya adalah, contoh; ketika dipanggil menggunakan sebuah input standar yang dikoneksikan ke sebuah perangkat tty (_teletypewriter_), interpreter mengeksekusi _command_ secara interaktif. Contoh lain adalah, ketika interpreter dipanggil dengan file sebagai input standar, maka interpreter membaca dan mengeksekusi script dari file tersebut.

Selain menggunakan command `python3.10`, kita juga bisa mengaktifkan interpreter dengan menuliskan `python -c command [arg] ...`, yang langsung mengeksekus _statement(s)_ yang dituliskan pada _command_. Beberapa _module_ Python berfungsi sebagai _script_. _modules_ tersebut dapat dipanggil dengan perintah `python -m module [arg] ...`,  yang mengeksekusi _source file_ untuk _module_.

Jika ingin lebih tahu banyak tentang berbagai opsi _command line_, kita bisa lihat di [Command line and environment](https://docs.python.org/3/using/cmdline.html#using-on-general).

### 2.1.1. Argument Passing
Nama script dan argumen-argumen tambahan selanjutnya akan dibubah menjadi sebuah list string dan dialokasikan ke variabel `argv` di dalam module `sys`. Kita bisa mengakses list ini dengan mengeksekusi `import sys`. Beberapa poin tentang argument passing:

 - Panjang sebuah list setidaknya adalah satu.
 - Jika tidak ada script dan argumen, maka `sys.argv[0]` dianggap sebagai _empty string_.
 - Jika nama script diberikan sebagai `'-'`(_standard input_), `sys.argv[0]` diset sebagai `'-'`.
 - Jika -c _command_  digunakan, `sys.argv[0]` diset sebagai `'-c'`
 - Jika -m _module_ digunakan, `sys.argv[0]` akan diset menjadi nama lengkap dari lokasi module tersebut.
 - Opsi yang terletak setelah -c _command_ atau -m _module_ tidak akan diproses oleh Python interpreter, tetapi diletakkan di `sys.argv`.

### 2.1.2. Interactive Mode
Di dalam mode ini, interpreter akan _prompt_ untuk _command_ selanjutnya dengan _primary prompt_ dengan tanda `(>>>)`; dan untuk baris-baris selanjutnya interpreter _prompt_ dengan _secondary prompt_ dengan tanda `(`...`)`. Berikut tampilan ketika interpreter menampilkan sebuah _welcome message_ sebelum prompt pertama:

    $ python3.10
    Python 3.10.2 (main, Feb  5 2022, 12:29:58) [GCC 9.3.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

_continuation lines_ berfungsi ketika statement telah memasuki sebuah _multi-line_. Contoh:

 _**nama file: `2.1.2.py`**_
```python
>>> the_world_is_flat = True
>>> if the_world_is_flat:
...     print("Be careful not to fall off!")
...     
Be careful not to fall off!
```
## 2.2. Interpreter dan Environment-nya.
### 2.2.1 Source Code Encoding
Secara default, _encoding_ untuk _source code_ Python adalah UTF-8. Untuk menampilkan semua karakter di _encoding_ itu, editor yang kita gunakan harus tahu bahwa file tersebut adalah UTF-8 dan editor juga harus menggunakan font yang _support_ semua karakter di file tersebut.

untuk mendeklarasikan encoding (selain encoding default UTF-8), kita harus menuliskan baris untuk _"special comment"_ pada baris pertama sebuah file. Berikut syntax-nya:

 _**nama file: `2.2.1.py`**_
```python
# -*- coding: encoding -*-
```

Contoh; untuk mendeklarasikan Windows-1252 encoding sebagai encoding yang akan digunakan, kita harus menuliskan berikut di baris pertama file:

_**nama file: `2.2.1.py`**_
```python
# -*- coding: cp1252 -*-
```

Ada satu pengecualian terhadap aturan deklarasi encoding _first line_ yaitu ketika code dimulai dengan [UNIX "shebang" line](https://docs.python.org/3/tutorial/appendix.html#tut-scripts). Pada kasus ini, deklarasi encoding harus dituliskan di baris kedua file, contoh:

_**nama file: `2.2.1.py`**_
```python
#!/usr/bin/env python3
# -*- coding: cp1252 -*-
```
<br/>

# 3. PENGANTAR INFORMAL TERHADAP BAHASA PEMROGRAMAN PYTHON
Input dan output pada bagian ini dibedakan dengan hadir atau tidaknya _prompts_ (`>>>` dan `...`). Input adalah segala baris yang kita tulis setelah prompt, sementara output adalah baris yang kemunculannya tidak dimulai dengan prompt.

Pertama-tama, kita bahas tentang _comments_. _Comments_ di Python dimuali dengan karakter _hash_ (#) dan akan berakhir di akhir baris yang diberi tanda _hash_ tersebut. Berikut contohnya:

```python
# ini adalah comment pertama
spam = 1 # ini adalah comment kedua
         # comment ketiga!
text = "# ini bukan komen karena berada di dalam quotes (tanda petik)"
```

## 3.1. Menggunakan Python Sebagai Kalkulator
### 3.1.1 Numbers
Interpreter berfungsi sebagai kalkulator sederhana. Operator seperti +, -, * dan / berfungsi sama seperti di bahasa pemrograman lain. Parentheses (()) dapat digunakan untuk _grouping_. Contoh:

_**nama file: `3.1.1-1.py`**_
```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # pembagian selalu me-return angka float
1.6
```
Division (/) selalu me-return float. Untuk melakukan [floor division](https://docs.python.org/3/glossary.html#term-floor-division) dan mendapatkan hasil integer, kita bisa menggunakan operator //. Untuk menghitung sisa pembagian bisa kita gunakan %.

_**nama file: `3.1.1-2.py`**_
```python
>>> 17 / 3 # pembagian biasa me-return float
5.666666666666667
>>> 17 // 3 # floor division menghilangkan bagian pecahan
5
>>> 17 % 3 # operator % me-return sisa pembagian
2
>>> 5 * 3 + 2 # hasil bagi floor division * pembagi + sisa pembagian
17
```
dengan Python, kita bisa menggunakan ** untuk menghitung hasil perpangkatan

_**nama file: `3.1.1-3.py`**_
```python
>>> 5 ** 2 # 5 kuadrat
25
>>> 2 ** 7 # 2 pangkat 7
128
```
tanda sama dengan (=) digunakan untuk menetapkan value ke dalam variabel.

_**nama file: `3.1.1-4.py`**_
