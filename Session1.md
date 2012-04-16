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

## Numeric Types and Mathematical Expressions
## Boolean Expressions
## Conditional Constructs
## Arrays
## Loop Constructs
## Code Blocks
## Ranges
## Regular Expressions
## Symbols
## Hashes
## Methods
