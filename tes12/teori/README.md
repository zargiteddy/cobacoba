# Jupyter

Install jupyter terlebih dahulu dengan perintah berikut:

```python
(workshop) zargiteddy@shield:~$ conda install -c anaconda jupyter
```

Buka jupyter notebook:

```python
(workshop) zargiteddy@shield:~$ jupyter notebook
[I 09:07:46.833 NotebookApp] Writing notebook server cookie secret to /home/zargiteddy/.local/share/jupyter/runtime/notebook_cookie_secret
[I 09:07:47.366 NotebookApp] Serving notebooks from local directory: /home/zargiteddy
[I 09:07:47.366 NotebookApp] Jupyter Notebook 6.4.8 is running at:
[I 09:07:47.366 NotebookApp] http://localhost:8888/?token=f0bb8690e46a3805226983884500d9de1bd8b490aa24838c
[I 09:07:47.366 NotebookApp]  or http://127.0.0.1:8888/?token=f0bb8690e46a3805226983884500d9de1bd8b490aa24838c
[I 09:07:47.366 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 09:07:47.494 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///home/zargiteddy/.local/share/jupyter/runtime/nbserver-5245-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=f0bb8690e46a3805226983884500d9de1bd8b490aa24838c
     or http://127.0.0.1:8888/?token=f0bb8690e46a3805226983884500d9de1bd8b490aa24838c
```
Setelah membuka notebook, kerjakan materi minggu 3 (bab 5).

----------------------------

## STRUKTUR DATA

### 5.1. Lebih Banyak tentang List

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
```python
In [1]: banana', 'kiwi', 'apple', 'banana']
        fruits.count('apple')
Out[1]: 2
In [2]: fruits.count('tangerine')
Out[2]: 0
In [3]: fruits.index('banana')
Out[3]: 3
In [4]: fruits.index('banana', 4) # mencari banana dimulai dari posisi 4
Out[4]: 6
In [5]: fruits.reverse()
        fruits
Out[5]: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
In [6]: fruits.append('grape')
        fruits
Out[6]: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
In [7]: fruits.sort()
        fruits
Out[7]: ['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
In [8]: fruits.pop()
Out[8]: 'pear'
In [9]: squares = []
            for x in range(10):
            squares.append(x**2)
In[10]: 



 

