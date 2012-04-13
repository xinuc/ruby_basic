# Session 1: Dasar Ruby

## Ruby Overview

Ruby adalah bahasa pemrograman berorientasi object murni yang dikembangkan oleh Yukihiro Matsumoto (Matz) pada tahun 1993.  Ruby merupakan bahasa interpreted, yang berarti untuk menjalankan ruby tidak perlu dicompile, tetapi cukup dijalankan dalam interpreternya.  Ruby juga merupakan bahasa dinamis. Kita tidak perlu melakukan deklarasi variable, tetapi cukup melakukan assignment secara langsung.

Ruby dibuat dengan tujuan untuk membuat programmer lebih bahagia. Artinya ruby dirancang untuk mempermudah kerja dari programmer. Programmer tidak perlu melakukan banyak tugas yang dapat dilakukan oleh komputer, sehingga programmer menjadi lebih produktif. Keunggulan utama dari ruby adalah bahasa yang sangat ekspresif, yang mempermudah programmer untuk mengubah dari ide menjadi kode program.

Penggunaan ruby yang paling umum adalah untuk pemrograman web, dengan framework ruby on rails. Tetapi ruby adalah bahasa pemrograman umum yang dapat digunakan untuk semua keperluan programming, dari aplikasi web, desktop, scripting, hingga aplikasi mobile.

Ruby merupakan bahasa object oriented murni. Dalam ruby, tidak ada tipe primitif. Semua adalah object, termasuk integer, string, array, class dan sebagainya.

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

Irb sangat berguna untuk mencoba kode dan melihat hasilnya dengan cepat. Namun untuk membuat program yang sebenarnya, kita akan menyimpan kode ruby kita dalam file, yang biasanya ber ekstensi .rb.

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

## Object-Oriented in Ruby: Classes, Attributes, Methods

Ruby adalah bahasa object oriented murni. Semuanya dari integer hingga string adalah object. Setiap object memiliki *methods* yang dapat dipanggil untuk melakukan berbagai fungsi. Untuk memanggil method, kita menggunakan syntax titik (.) yang diikuti oleh nama methodnya. Contohnya, jika kita ingin mengubah kalimat "hello world" menjadi huruf kapital, kita bisa memanggil method *upcase*

```ruby
  puts "hello world".upcase
```

Beberapa method, seperti *puts* dan *gets* dapat dipanggil dimanapun dan tidak perlu digabungkan dengan object tertentu. Method - method ini ada di dalam modul *Kernel* bawaan ruby, yang di *include* di dalam semua object ruby. Ketika kita menjalankan aplikasi ruby, sebuah object dengan nama *main* dibuat secara otomatis dan memberikan kita akses ke semua method dalam module *Kernel*

## String Type and Operations
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
