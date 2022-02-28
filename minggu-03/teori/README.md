# 5. STRUKTUR DATA
Bab ini berisi tentang penjelasan beberapa materi yang sebelumnya sudah kita pelajari, tetapi dengan lebih detail dan juga ada beberapa tambahan materi.

## 5.1. List: Tambahan
List memiliki beberapa method. Berikut method-method milik objek list:
- list.**append**_(x)_ = berguna untuk menambahkan sebuah item pada akhir list. Setara dengan `a[len(a):] = [x]`.
- list.**extend**_(iterable)_ = memperbesar list dengan cara menambahkan seluruh item dari _iterable_ (objek yang memiliki iterator). Setara dengan `a[len(a):] = iterable`
- list.**insert**_(i, x)_ = memasukkan item pada posisi yang sudah ditentukan. Argumen pertama adalah index dari elemen yang akan dimasukkan sebelumnya. Jadi, `a.insert(0, x)` masuk pada sisi paling depan sebuah list, dan `a.insert(len(a), x)` setara dengan `a.append(x)`.
- list.**remove**_(x)_ = menghapus item pertama pada sebuah list. Item yang dihapus adalah item yang nilainya adalah `x`. Jika tidak ada item tersebut, maka akan muncul [ValueError](https://docs.python.org/3/library/exceptions.html#ValueError).
- list.**pop**_([i])_ = menghapus item pada posisi tertentu pada sebuah list, dan di-return. Jika tidak ada indeks yang ditetapkan, maka `a.pop()` menghapus dan me-return item terakhir dalam list.
- list.**clear**_()_ = menghapus semua item pada list. Setara dengan `del a[:]`.
- list.**index**_(x[, start[, end]])_ = me-return _zero-based index_ pada list item pertama yang nilainya sama dengan `x`. Jika tidak ada item tersebut maka akan muncul [ValueError](https://docs.python.org/3/library/exceptions.html#ValueError).
- list.**count**_(x)_ = me-return jumlah berapa kali `x` muncul dalam list.
- list.**sort**_(, key=None, reverse=False)_ = mengurutkan item pada sebuah list dengan _ascending_ atau _descending_ (defaultnya adalah _ascending_). Untuk penjelasan lebih lanjut tentang sort bisa lihat di [sorted](https://docs.python.org/3/library/functions.html#sorted).
- list.**reverse**_()_ = memutar balik elemen yang ada pada sebuah list.
- list.**copy**_()_ = me-return _shallow copy_ (salinan) list. Setara dengan `a[:]`

Berikut contoh penggunaan method list:

_**nama file: `5.1.py`**_
```python
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple')
2
>>> fruits.count('tangerine')
0
>>> fruits.index('banana')
3
>>> fruits.index('banana', 4) # mencari banana dimulai dari posisi 4
6
>>> fruits.reverse()
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
>>> fruits.append('grape')
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
>>> fruits.sort()
>>> fruits
['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
>>> fruits.pop()
'pear'
```
Bisa kita perhatikan jika method-method yang hanya memodifikasi list seperti `insert`, `remove`, atau `sort` tidak menampilkan _return value_. Method-method tersebut me-return nilai default yaitu `None`. Hal ini merupakan prinsip desain seluruh struktur data _mutable_(data yang elemennya bisa diubah) pada Python.

Selain itu, bisa juga kita perhatikan bahwa tidak semua data bisa di-sort (diurutkan) atau dibandingkan. Contohnya, `[None, 'hello', 10]` tidak bisa diurutkan karena integer tidak dapat dibandingkan dengan string. `None` juga tidak dapat dibandingkan dengan tipe data lain.

### 5.1.1. Menggunakan List sebagai Stack ###
Method-method list dapat mempermudah untuk menggunakan list sebagai stack (tumpukan), yaitu elemen terakhir yang ditambahkan merupakan elemen pertama yang diterima (LIFO / last-in first-out). Untuk menambahkan sebuah item di atas stack, kita bisa gunakan `append()`. Untuk mengambil sebuah item dari atas stack, kita bisa gunakan `pop()` tanpa index eksplisit. Contoh:

_**nama file: `5.1.1.py`**_
```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```
- - - - - - -
### 5.1.2. Menggunakan List sebagai Queue ###
Kita juga bisa menggunakan list sebagai queue (antrian), yaitu elemen pertama yang ditambahkan merupakan elemen pertama yang diterima (FIFO / first-in, first-out). Walaupun begitu, penerapan queue ini tidak efisien untuk list. Kenapa? Karena _append_ dan _pop_ dari akhir list akan berjalan dengan cepat, sementara melakukan _insert_ dan _pop_ dari awal list akan berjalan dengan lambat. 

Untuk menerapkan queue, kita bisa gunakan [collections.deque](https://docs.python.org/3/library/collections.html#collections.deque) yang didesain untuk melakukan proses _append_ dan _pop_ dengan cepat dari sisi manapun. Contoh:

_**nama file: `5.1.2.py`**_
```python
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry") # Terry masuk
>>> queue.append("Graham") # Graham masuk
>>> queue.popleft() # Pertama masuk sekarang keluar
'Eric'
>>> queue.popleft() # Kedua masuk sekarang keluar
'John'
>>> queue # Sisa antrian yang diurutkan berdasarkan kedatangan
deque(['Michael', 'Terry', 'Graham'])
```
- - - - - - -
### 5.1.3. List Comprehensions ###
_List comprehensions_ menyediakan cara yang pendek dan efisien dalam membuat list. List comprehension biasanya digunakan untuk membuat list baru dari elemen-elemen list yang sudah ada. Dengan list comprehension, kita bisa membuat loop dengan lebih jelas dan kita bisa membuat list secara otomatis dalam satu _command line_ saja.

Misalnya adalah ketika kita ingin membuat list berisi hasil kuadrat:

_**nama file: `5.1.3-1.py`**_
```python
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
Bisa kita perhatikan bahwa pembuatan list tersebut menghasilkan sebuah variabel bernama x yang masih ada ketika loop selesai. Kita juga bisa menghitung list tersebut dengan menggunakan cara ini:
```python
squares = list(map(lambda x: x**2, range(10)))
```
atau:
```python
squares = [x**2 for x in range(10)]
```
- - - - - - - -
List comprehension terdiri dari _bracket_ yang berisi sebuah expresi yang diikuti dengan klausa `for`, lalu dilanjut dengan klausa `for` atau `if` bernilai nol atau lebih. Hasilnya adalah sebuah list baru yang dihasilkan dari perhitungan expresi tersebut. Contohnya adalah saat listcomp (list comprehension) menggabungkan dua elemen dari dua list jika kedua elemen tersebut tidak sepadan:

_**nama file: `5.1.3-2.py`**_
```python
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```
sepadan dengan:
```python
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```
- - - - - - -
Jika ekspresi berupa tuple, maka kita perlu parentheses (diletakkan di dalam kurung):

_**nama file: `5.1.3-3.py`**_
```python
>>> vec = [-4, -2, 0, 2, 4]
>>> # buat list baru yang nilainya dikali dua
>>> [x*2 for x in vec]
[-8, -4, 0, 4, 8]
>>> # melakukan filter pada list untuk meniadakan angka negatif
>>> [x for x in vec if x >= 0]
[0, 2, 4]
>>> # terapkan fungsi ke semua elemen
>>> [abs(x) for x in vec]
[4, 2, 0, 2, 4]
>>> # panggil method pada setiap elemen
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
>>> # buat list 2-tuples seperti (number, square)
>>> [(x, x**2) for x in range(6)]
[(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
>>> # tuple harus di-parenthesized, jika tidak maka akan muncul error.
>>> [x, x**2 for x in range(6)]
  File "<stdin>", line 1, in <module>
    [x, x**2 for x in range(6)]
               ^
SyntaxError: invalid syntax
>>> # memaparkan list menggunakan listcomp dengan dua 'for'
>>> vec = [[1,2,3], [4,5,6], [7,8,9]]
>>> [num for elem in vec for num in elem]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```
- - - - - - -
List comprehensions juga dapat berisi ekspresi yang kompleks dan fungsi _nested_:

_**nama file: `5.1.3-4.py`**_
```python
>>> from math import pi
>>> [str(round(pi, i)) for i in range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```
- - - - - 
### 5.1.4. Nested List Comprehensions ###
Expresi pertama pada sebuah list comprehension bisa berupa ekspresi arbitrary (ekspresi yang dipilih/digunakan sesuai dengan keinginan personal user), atau juga bisa berupa list comprehension lain.

Contoh berikut adalah matriks 4x4 yang diimplementasikan sebagai 3 list yang masing-masing memiliki length 4:

_**nama file: `5.1.4.py`**_
```python
>>> matrix = [
...     [1, 2, 3, 4],
...     [5, 6, 7, 8],
...     [9, 10, 11, 12],
... ]
```
list comprehension berikut akan mengubah urutan baris dan kolom:
```python
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
Seperti yang kita lihat pada _section_ sebelumnya, _nested listcomp_ dievalueasi di dalam konteks for yang mengikuti _nested listcomp_. Jadi contoh tersebut sama dengan:
```python
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
yang juga sama dengan:
```python
>>> transposed = []
>>> for i in range(4):
...     # 3 baris di bawah digunakan untuk implementasi nested listcomp
...     transposed_row = []
...     for row in matrix:
...         transposed_row.append(row[i])
...     transposed.append(transposed_row)
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
Kita harus menggunakan fungsi built-in untuk statement flow yang kompleks. Kita bisa menggunakan fungsi [zip()](https://docs.python.org/3/library/functions.html#zip) :
```python
>>> list(zip(*matrix))
[(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```
## 5.2. Statement `del`