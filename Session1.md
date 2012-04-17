# Session 1: Dasar Ruby

## Ruby Overview

Ruby adalah bahasa pemrograman berorientasi object murni yang dikembangkan oleh Yukihiro Matsumoto (Matz) pada tahun 1993.
Ruby merupakan bahasa interpreted, yang berarti untuk menjalankan ruby tidak perlu dicompile, tetapi cukup dijalankan dalam interpreternya.
Ruby juga merupakan bahasa dinamis. Kita tidak perlu melakukan deklarasi variable, tetapi cukup melakukan assignment secara langsung.

Ruby dibuat dengan tujuan untuk membuat programmer lebih bahagia. Artinya ruby dirancang untuk mempermudah kerja programmer.
Programmer tidak perlu melakukan banyak tugas yang dapat dilakukan oleh komputer, sehingga programmer menjadi lebih produktif.
Keunggulan utama dari ruby adalah bahasa yang sangat ekspresif, yang mempermudah programmer untuk mengubah dari ide menjadi kode program.

Penggunaan ruby yang paling umum adalah untuk pemrograman web, dengan framework ruby on rails.
Tetapi ruby adalah bahasa pemrograman umum yang dapat digunakan untuk semua keperluan programming,
dari aplikasi web, desktop, scripting, hingga aplikasi mobile.

Ruby merupakan bahasa object oriented murni. Dalam ruby, tidak ada tipe primitif.
Semua adalah object, termasuk integer, string, array, class dan sebagainya.

Berikut ini adalah contoh program hello world di ruby:

```ruby
  puts "Hello world"
```

## Menjalankan ruby

Cara paling mudah untuk mencoba ruby adalah dengan menggunakan irb (interactive ruby).

```
   $ irb
   > 3 + 5
   => 8
   > puts "hello " * 3
   hello hello hello
   => nil
```

Irb sangat berguna untuk mencoba kode dan melihat hasilnya dengan cepat.
Namun untuk membuat program yang sebenarnya, kita akan menyimpan kode ruby kita dalam file, yang biasanya berekstensi .rb.

``` ruby
  # file: hello.rb
  4.times do
    puts "hello"
  end
```

kemudian kita jalankan dengan perintah `ruby <nama file>`

```
  $ ruby hello.rb
  hello
  hello
  hello
  hello
```
## Syntax dan Idiom

Program yang ditulis dengan ruby pada umumnya mudah dibaca. Hal ini dikarenakan ruby memiliki syntax yang bersih dan sederhana.
Readability program juga terbantu jika programmer mengikuti idiom yang umum digunakan dalam ruby.

Berikut ini adalah contoh program sederhana dalam ruby:

``` ruby
  class Person
    attr_accessor :first_name, :last_name, :age

    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end

    def fullname
      @first_name + " " + @last_name
    end

    def mature?
      @age > 17
    end

    def increase_age!
      @age += 1
    end
  end

  person = Person.new "Slamet", "Riyadi"
  person.age = 17
  person.full_name     # "Slamet Riyadi"
  person.increase_age! # @age == 18
  person.mature?       # true
```

Untuk membuat kelas, kita menggunakan kata kunci `class` diikuti dengan nama kelas. Nama kelas dalam ruby harus dimulai dengan huruf kapital.
Idiom yang biasa dipakai adalah menggunakan *CamelCase* untuk nama kelas.

contoh: `PurchasedItem`, `ProductsInventory`

Kata kunci `def` digunakan untuk mendefinisikan method didalam suatu kelas atau modul.
Pada umumnya, kita menggunakan huruf kecil dan *underscore* (_) sebagai nama method (biasa disebut *snake_case*).
Nama method dapat mempunyai tanda baca seperti `?, !, =` pada bagian akhir.
Tanda tanya (?) biasa digunakan dalam nama method yang mereturn boolean, sedangkan tanda seru (!) digunakan dalam
method yang dianggap berbahaya, biasanya method yang dapat mengubah nilai.

contoh: `products_list`, `buy!`, `available?`

Penamaan menggunakan *snake_case* digunakan hampir di semua hal dalam ruby selain nama kelas dan konstant.
Instant variable selalu diawali dengan tanda `@`.  Object diinisiasi dengan memanggil method `new` pada kelasnya.
Pada umumnya programmer ruby selalu menggunakan indentasi 2 spasi dan tidak pernah menggunakan indentasi tab.

## Object-Oriented in Ruby: Classes, Attributes, Methods

Ruby adalah bahasa object oriented murni. Semuanya dari integer hingga string adalah object.
Setiap object memiliki *methods* yang dapat dipanggil untuk melakukan berbagai fungsi.
Untuk memanggil method, kita menggunakan syntax titik (.) yang diikuti oleh nama methodnya.
Contohnya, jika kita ingin mengubah kalimat "hello world" menjadi huruf kapital, kita bisa memanggil method *upcase*

```ruby
  puts "hello world".upcase
```

Beberapa method, seperti *puts* dan *gets* dapat dipanggil dimanapun dan tidak perlu digabungkan dengan object tertentu.
Method - method ini ada di dalam modul *Kernel* bawaan ruby, yang di *include* di dalam semua object ruby.
Ketika kita menjalankan aplikasi ruby, sebuah object dengan nama *main* dibuat secara otomatis dan memberikan kita akses
ke semua method dalam module *Kernel*

## String Type and Operations

String adalah object ruby yang berfungsi memanipulasi rangkaian byte, yang pada umumnya mereprensentasikan huruf - huruf
dalam suatu kalimat. Ruby memiliki kelas built-in yang bernama `String` yang memiliki beberapa method yang sering kita
gunakan dalam memprogram ruby.

Berikut ini adalah fungsi - fungsi yang terkait dengan String dalam ruby:

### String declaration

Pada umumnya sebuah string dideklarasikan dengan rangkaian huruf yang dibatasi oleh tanda
petik ganda (") atau tunggal (').

contoh: `"ini adalah sebuah string"`, `'ini juga'`

String juga dapat dideklarasikan dengan menggunakan *general delimiter* berupa yang diawali oleh
`%`, `%Q`, atau `%q`.

contoh:

```ruby
%{ String menggunakan general delimiter }
%Q{ String menggunakan general delimiter }
```

Untuk membuat string lebih dari satu baris, akan lebih mudah menggunakan syntax sebagai berikut:

```ruby
multiline_string = <<-STR
  ini adalah string
  lebih dari satu baris
STR
```

### Expression subtitution

Expression subtitution adalah suatu cara untuk menggabungkan hasil dari suatu ekspresi ruby ke dalam suatu string
menggunakan #{ dan }:

```ruby
  name = "Ruby"
  a = 7
  b = 3
  puts "my name is #{name}"       # my name is Ruby
  puts "#{a} + #{b} = #{ a + b }" # 7 + 3 = 10
```

### String methods

Berikut ini adalah beberapa method yang dimiliki String object yang sering kita gunakan:

* `str + other_str`
  menggabungkan other_str ke str, menghasilkan object baru hasil gabungan kedua string tersebut.

* `str << other_str`
  menggabungkan other_str ke str, mengubah object str (tidak menghasilkan object baru).

* `str <=> other_str`
  membandingkan dua string, menghasilkan -1 jika str lebih kecil dari other_str, 1 jika str
  lebih besar dari str, dan 0 jika str sama dengan other_str

* `str == other_str`
  membandingkan kesamaan dua string, menghasilkan `true` jika sama, `false` jika tidak sama.

* `str =~ regex`
  membandingkan string dengan regular expression, menghasilkan posisi pertama kesesuaian jika ada,
  atau 0 jika tidak sesuai.

* `str.capitalize`
  mengubah huruf pertama menjadi huruf kapital, menghasilkan object baru.

* `str.capitalize!`
  mengubah huruf pertama menjadi huruf kapital dengan mengubah object yang ada.

* `str.upcase`
  mengubah semua huruf menjadi huruf kapital, menghasilkan object baru.

* `str.upcase!`
  mengubah semua huruf menjadi huruf kapital dengan mengubah object yang ada.

* `str.length`
  menghasilkan panjang string.

* `str.strip`
  menghapus whitespace yang ada di depan dan di belakang string.

## Numeric

Dalam ruby, angka bukanlah primitive. Setiap angka adalah object, instance dari salah satu kelas
numeric ruby. `Numeric` adalah kelas basis untuk angka di ruby. Kelas `Fixnum` digunakan untuk
integer, `Float` untuk angka pecahan, dan `Bignum` untuk angka integer yang lebih besar.

Konversi antara angka `Fixnum` dan `Bignum` terjadi secara otomatis. Ketika suatu angka tidak
dapat disimpan dalam `Fixnum`, akan secara otomatis diubah ke `Bignum`, sehingga kita sebagai
programmer tidak perlu memikirkannya.

contoh:

```ruby
  2411 # integer, Fixnum
  2_411 # integer, Fixnum, underscore diabaikan
  241.1 # pecahan, Float
  3.7e4 # scientific notation, Float
  3E4 # scientific notation, Float
  3E-4 # scientific notation, dengan tanda sebelum exponent
  0444 # octal, Fixnum
  0xfff # hexadecimal, Fixnum
  0b1101 # binary, Fixnum
  4567832704 # integer, Bignum
```

## Boolean

Ruby memiliki nilai boolean `true` dan `false`, yang merupakan object dari kelas `TrueClass` dan `FalseClass`.
Dalam ruby, semua nilai selain `false` dan `nil` dianggap bernilai true dan dapat digunakan dalam operasi
boolean, seperti conditional, `and`, `or` dan sebagainya.

## Conditional Constructs

Conditional statement mengecek apakah suatu ekspresi bernilai benar atau salah dan menjalankan logic sesuai
dengan hasil dari ekspresi tersebut.

### If statement

If statement diawali dengan keyword `if` dan diakhiri dengan keyword `end`.

```ruby
  if 3 > 2
    puts "Tiga lebih besar dari dua"
  end
```

Operator `!` membalikkan nilai `true / false` suatu ekspresi.

```ruby
  if !(x > y)
    puts "X tidak lebih besar dari y"
  end
```

Kita dapat menggunakan operasi boolean dalam if statement untuk mengecek dua ekspresi atau lebih
menggunakan `&& (and)` dan `|| (or)`.

```ruby
  if ruby == "great" && programming == fun
    puts "I love programming with ruby"
  end
```

Jika ekspresi cukup pendek, kita dapat meletakkan if statement di belakang sebagai modifier.

```ruby
  puts "Tiga lebih besar dari dua" if 3 > 2
```

`else` dan `elsif` dapat ditambahkan sebagai opsi jika statement `if` tidak benar.

```ruby
  if x > y
    puts "x lebih besar dari y"
  elsif x < y
    puts "x lebih kecil dari y"
  else
    puts "x sama dengan y"
  end
```

Jika kita mengecek negasi dari suatu expresi, akan lebih jelas jika kita memakai `unless` daripada menggunakan operator `!`

```ruby
  unless x == y
    puts "x tidak sama dengan y"
  end
```

Seperti `if`, `unless` juga dapat kita letakkan di belakang sebagai modifier.

```ruby
  puts "Tiga tidak lebih besar dari dua" unless 3 > 2
```

### While statement

While loop digunakan untuk mengeksekusi suatu blok kode selama nilai conditionalnya `true`.

```ruby
  i = 0
  while i < 10
    puts "hello"
    i += 1
  end
```

### Until statement

Sebagaimana `unless` adalah negasi dari `if`, statement `until` adalah negasi dari `while`, yaitu
akan mengeksekusi blok kode sampai nilai conditionalnya menjadi `true`.

```ruby
  i = 0
  until i >= 10
    puts "hello"
    i += 1
  end
```


Pada prakteknya, kita akan sangat jarang menggunakan `while` dan `until` untuk melakukan loop.
Kita akan lebih sering melakukan iterasi menggunakan method `each` yang dimiliki suatu array / koleksi.

### Case statement

Statement `case` dan `when` dalam ruby memberikan cara untuk mengekspresikan conditional logic dalam bentuk
yang sangat ringkas. `case` mirip dengan `switch` dalam bahasa pemrograman lain, tetapi `case` dapat
mengecek semua tipe object yang dapat dibandingkan kesamaannya atau ekuivalensinya.

Menggunakan `case` statement lebih ringkas daripada menggunakan `if else` karena kita berasumsi membandingkan
kesamaan dengan `==`.

```ruby
  lang = "fr"
  dog = case lang
    when "en"
      "dog"
    when "es"
      "perro"
    when "fr"
      "chien"
    when "de"
      "Hund"
    else
      "dog"
  end
```

`case` dapat digunakan untuk melakukan perbandingan nilai dalam range tertentu

```ruby
  scale = 8
  case scale
    when 0
      puts "lowest"
    when 1..3
      puts "medium-low"
    when 4..5
      puts "medium"
    when 6..7
      puts "medium-high"
    when 8..9
      puts "high"
    when 10
      puts "highest"
    else
      "oputsff scale"
  end
```

### Operator ternary

Operator ternary (?:) adalah struktur yang diwarisikan dari C ke ruby. Operator ini merupakan bentuk pendek
dari `if else` statement.

```ruby
  size = length > 100 ? "Big" : "Small"
```

## Arrays

Array adalah salah satu kelas bawaan ruby. Array adalah suatu koleksi object yang berurutan dan dapat
diakses berdasarkan indexnya. Dalam ruby, array dapat menyimpan semua object seperti String, Fixnum,
Hash bahkan array yang lain. Setiap elemen di dalam array diasosiasikan dan diakses dengan index
tertentu. Elemen - elemen array secara otomatis diindex dengan angka dimulain dari 0.
Kita dapat mengakses elemen terakhir dari array dengan menggunakan index -1,
kedua dari belakang dengan -2 dan seterusnya. Ukuran array di ruby dinamis dan dapat bertambah sesuai
dengan kebutuhan secara otomatis.

### Inisiasi array

Ada beberapa cara untuk membuat / menginisiasi suatu array. Yang pertama adalah dengan memanggil method
`new` pada kelas `Array`

```ruby
  months = Array.new
```

Kita dapat menentukan panjang awal suatu array ketika inisiasi.

```ruby
  months = Array.new 12
```
Array `months` sekarang memiliki panjang 12.

Kita juga dapat melihat berapa panjang dari sebuah array.

```ruby
  months.size # 12
  #atau
  months.length # 12
```

Tetapi cara yang paling mudah dan paling umum digunakan untuk menginisiasi sebuah array adalah dengan
menggunakan literal `[]` dan mengisi elemennya secara langsung.

```ruby
  months = ["January", "February", "March"]
```

### Array methods

Berikut ini adalah beberapa method penting yang sering kita pakai:

* `array + other_array`
  mereturn array baru dengan menggabungkan kedua array.

* `array - other_array`
  mereturn array baru dengan menghapus semua elemen `array` yang muncul di `other_array`.

* `array << object`
  memasukkan `object` ke akhir array.

* `array == other_array`
  mengecek apakah `array` memiliki elemen yang sama (yang masing-masing dibandingkan dengan method `==`)
  dengan `other_array`

* `array <=> other_array`
  mereturn integer (-1, 0 atau 1) berdasarkan perbandingan elemen-elemen dalam kedua array

* `array[index]`
  mereturn elemen pada `index`, menghasilkan nil jika tidak ada elemen pada index tersebut.

* `array.each{|item| block}`
  menjalankan block untuk setiap elemen array, menggunakan elemen array tersebut sebagai parameter.

* `array.map{|item| block}`
  menjalankan block untuk setiap elemen array, dan menghasilkan array baru dengan elemen hasil eksekusi blok tersebut.

## Code Blocks

Sebuah _block_ dapat dianggap sebagai sebuah method yang tidak memiliki nama.
Block dalam ruby dapat ditulis di dalam _brackets_ `{...}` atau `do...end`.
Konsep block sering dipakai dalam ruby, misalnya dalam beberapa method milik array.

```ruby
[1,2,3].each do |item|
  puts item
end
```

Block juga berperilaku sebagai _closure_, yaitu kode dalam sebuah block dapat mengakses variabel diluarnya,
tetapi kode di luar block tidak dapat mengakses variabel lokal dalam block tersebut.

```ruby
prefix = "print "
[1,2,3].each do |item|
  puts prefix
  puts item
end

puts item # error
```

## Ranges

_Range_ memberikan cara mudah untuk merepresentasikan urutan alfanumerik (angka dan huruf).
Range dapat digunakan sebagai sekuens maupun untuk pengecekan interval.

```ruby
one_to_ten = 1..10
a_to_z = "a".."z"
a0_to_z9 = "a0".."z9"
```

### Range Sebagai Sekuens

Range dapat diperlakukan sebagai array dan diiterasi:

```ruby
(1..20).each do |num|
  puts num
end
```

Ukuran langkah tiap satuan item dapat ditentukan dengan method `step`

```ruby
(1..20).step(3).each do |num|
  puts num
end
```

### Range Sebagai Interval

Range dapat digunakan untuk menentukan apakah suatu angka/string termasuk dalam interval tertentu

```ruby
(1..20) === 22 # => false
```

Ini berarti range dapat digunakan dengan mudah dalam statement `case...when`

```ruby
num = 9001

case num
when 1..10
  puts "Below ten"
when 10..9000
  puts "Below nine thousand"
else
  puts "Over nine thousaaaand!!!"
end
```

## Regular Expressions

_Regular Expression_ dalam ruby ditangani oleh kelas `Regexp`. 
Untuk membentuk regular expression, sintaks yang digunakan sama dengan Perl.
Regular expression dalam ruby juga memiliki fitur string interpolation.

```ruby
movie_title_regexp = /^the/i

string = "the"
also_movie_title_regexp = /^#{string}/i # => /^the/i
```

Untuk mencocokan pola regular expression dengan sebuah string, bisa menggunakan method `=~` atau `[]` dari string.
`=~` mengembalikan indeks pola yang pertama kali cocok, sedangkan `[]` mengembalikan substring yang cocok.

```ruby
has_and = /and/i

"Sand Man" =~ has_and # => 1
"Sand Man"[has_and] # => "and"
```

## Symbols
## Hashes
## Methods
