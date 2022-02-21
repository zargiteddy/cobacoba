# 4. CONTROL FLOW
Python menggunakan statement-statement control flow yang sama seperti di bahasa pemrograman lain, tetapi dengan beberapa perbedaan.

## 4.1. Pernyataan `if`
Statement yang paling terkenal adalah statement If. Contoh:

_**nama file: `4.1.py`**_
```python
>>> x = int(input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
...
More
```
Python memiliki statement kondisi yaitu `if`, `elif`, dan `else`. Kondisi `if` dapat digunakan untuk mengeksekusi kode yang bernilai `True`. Jika kondisi bernilai `False`, maka `if` tidak akan dianggap dan Python akan mengeksekusi kode milik `elif` atau `else`. 

Di Python ada satu statement kondisi yang penulisannya berbeda dari kebanyakan bahasa pemrograman yaitu `elif`. keyword `elif` merupakan kependekan dari `else if`. statement `elif` ini berguna untuk menghindari indentasi yang berlebihan atau kelewatan. Sementara _sequence_ `if … elif … elif …` merupakan pengganti dari `switch` atau `case` yang biasa ditemukan di bahasa pemrograman lain.

## 4.2. Pernyataan `for`
Statement `for` di Python berbeda dengan `for` di bahasa pemrograman lain seperti C atau Pascal. Di Python, `for` melakukan perulangan pada item-item milik _sequence_ seperti list atau string. Contoh:

_**nama file: `4.2-1.py`**_
```python
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
```
---------------------
Kita juga bisa melakukan perulangan pada sebuah _collection_ lalu membuat _collection_ baru:

_**nama file: `4.2-2.py`**_
```python
# Membuat sample colllection
users = {'Hans': 'active', 'Éléonore': 'inactive', '景太郎': 'active'}

# Strategi:  Lakukan iterasi pada salinan
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

# Strategy:  Buat collection baru
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```
## 4.3. Fungsi `range()`
Jika kita tidak perlu melakukan iterasi pada sebuah _sequence_ berisi angka, maka kita bisa menggunakan fungsi _built-in_ `range()`. Fungsi ini menghasilkan sebuah progresi aritmatika:

_**nama file: `4.3-1.py`**_
```python
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```
---------------------
Kita bisa membuat range memulai dari angka berapa saja atau menentukan _increment_ yang berbeda:

_**nama file: `4.3-2.py`**_
```python
>>> list(range(5, 10))
[5, 6, 7, 8, 9]

>>> list(range(0, 10, 3))
[0, 3, 6, 9]

>>> list(range(-10, -100, -30))
[-10, -40, -70]
```
---------------------
Untuk melakukan iterasi pada index sebuah _sequence_ kita bisa mengombinasikan fungsi `range()` dan `len()` seperti berikut:

_**nama file: `4.3-3.py`**_
```python
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```
Di beberapa kasus tertentu, ada baiknya kita menggunakan fungsi `enumerate()`. Silakan lihat di [Teknik Looping](https://docs.python.org/3/tutorial/datastructures.html#tut-loopidioms).
- - - - - - - -
Keanehan bisa terjadi ketika kita hanya melakukan print pada sebuah range:

_**nama file: `4.3-4.py`**_
```python
>>> range(10)
range(0, 10)
```
- - - - - - - -
Berikut contoh penggunaan `sum` dengan `range()`:

_**nama file: `4.3-5.py`**_
```python
>>> sum(range(4))  # 0 + 1 + 2 + 3
6
```
## 4.4. Pernyataan `break` dan `continue`, dan Klausa `else` pada Loop
Perintah `break` memaksa sebuah perulangan berhenti sebelum waktunya berhenti. Statement loop juga bisa memiliki sebuah klausa `else` yang dieksekusi ketika loop terhenti terjadi _exhaustion_ pada iterator (`for`) atau ketika kondisi bernilai `false` (`while`). Berikut contoh loop untuk menentukan bilangan prima:

_**nama file: `4.4-1.py`**_
```python
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop gagal tanpa menemukan faktor
...         print(n, 'is a prime number')
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```
Bisa kita lihat jika klausa `else` adalah milik `for`, bukan milik statement `if`.

Ketika digunakan dengan loop, klausa `else` lebih memiliki kemiripan dengan klausa `else` milik statement `try` daripada milik statement `if`.
- - - - - - - -
Pernyataan/statement `continue`, melanjutkan iterasi selanjutnya pada sebuah loop:

_**nama file: `4.4-2.py`**_
```python
>>> for num in range(2, 10):
...     if num % 2 == 0:
...         print("Found an even number", num)
...         continue
...     print("Found an odd number", num)
...
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9
```
## 4.5. Pernyataan `pass`
Pernyataan/statement `pass` tidak melakukan apapun. `pass` bisa digunakan jika sebuah statement dibutuhkan secara sintaks, tetapi program tidak memerlukan _action_ apapun. Contoh:

_**nama file: `4.5-1.py`**_
```python
>>> while True:
...     pass
...
```
- - - - - - -
`pass` juga biasanya digunakan untuk membuat _minimal class_:

_**nama file: `4.5-2.py`**_
```python
>>> class MyEmptyClass:
...     pass
...
```
- - - - - - -
`pass` juga bisa menjadi _place-holder_ untuk sebuah fungsi ketika kita sedang mengerjakan kode lain:

_**nama file: `4.5-3.py`**_
```python
>>> def initlog(*args):
...     pass   # Jangan lupa beri implementasi di sini!
...
```
## 4.6. Pernyataan `match`
Pernyataan/statement `match` berfungsi untuk membandingkan nilai dengan beberapa pola berbeda sampai cocok:

_**nama file: `4.6-1.py`**_
```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```
- - - - - - -
Kita bisa mengombinasikan beberapa literal hanya dalam satu _pattern_ menggunakan | (“or”):

_**nama file: `4.6-2.py`**_
```python
case 401 | 403 | 404:
    return "Not allowed"
```
- - - - - - -
Kita juga dapat mengikat beberapa variabel:

_**nama file: `4.6-3.py`**_
```python
# point adalah tuple (x, y)
match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"Y={y}")
    case (x, 0):
        print(f"X={x}")
    case (x, y):
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```
- - - - - - -
Jika kita menggunakan class untuk membangun data, kita bisa menggunakan nama class yang diikuti dengan argument list yang berperan sebagai konstruktor yang memiliki kemampuan untuk mengambil atribut ke dalam variabel:

_**nama file: `4.6-4.py`**_
```python
class Point:
    x: int
    y: int

def where_is(point):
    match point:
        case Point(x=0, y=0):
            print("Origin")
        case Point(x=0, y=y):
            print(f"Y={y}")
        case Point(x=x, y=0):
            print(f"X={x}")
        case Point():
            print("Somewhere else")
        case _:
            print("Not a point")
```
- - - - - - -
Kita bisa mendefinisikan posisi tertentu untuk atribut di dalam _pattern_ dengan mengatur `__match_args__` di class yang telah kita buat. Jika sudah ter-set menggunakan (“x”, “y”), maka seluruh _pattern_ selanjutnya akan bernilai sama:

_**nama file: `4.6-5.py`**_
```python
Point(1, var)
Point(1, y=var)
Point(x=1, y=var)
Point(y=var, x=1)
```
- - - - - - -
_Pattern_ dapat dibuat dalam bentuk _nested_. Contoh, jika kita memiliki list point yang pendek, kita bisa mencocokannya seperti ini:

_**nama file: `4.6-6.py`**_
```python
match points:
    case []:
        print("No points")
    case [Point(0, 0)]:
        print("The origin")
    case [Point(x, y)]:
        print(f"Single point {x}, {y}")
    case [Point(0, y1), Point(0, y2)]:
        print(f"Two on the Y axis at {y1}, {y2}")
    case _:
        print("Something else")
```
- - - - - - -
Kita bisa menambahkan klausa `if` pada _pattern_ yang bisa kita sebut sebagai "guard". Jika "guard" bernilai `false`, `match` akan mencoba block case selanjutnya:

_**nama file: `4.6-7.py`**_
```python
match point:
    case Point(x, y) if x == y:
        print(f"Y=X at {x}")
    case Point(x, y):
        print(f"Not on the diagonal")
```
- - - - - - -
_Subpatterns_ dapat diambil menggunakan keyword `as`:

_**nama file: `4.6-8.py`**_
```python
case (Point(x1, y1), Point(x2, y2) as p2): ...
```
- - - - - - -
_Patterns_ dapat menggunakan konstanta yang sudah diberi nama:

_**nama file: `4.6-9.py`**_
```python
from enum import Enum
class Color(Enum):
    RED = 'red'
    GREEN = 'green'
    BLUE = 'blue'

color = Color(input("Enter your choice of 'red', 'blue' or 'green': "))

match color:
    case Color.RED:
        print("I see red!")
    case Color.GREEN:
        print("Grass is green")
    case Color.BLUE:
        print("I'm feeling the blues :(")
```
Jika ingin melihat penjelasan yang lebih detail beserta contoh-contohnya, bisa langsung menuju [PEP 636](https://www.python.org/dev/peps/pep-0636/)





