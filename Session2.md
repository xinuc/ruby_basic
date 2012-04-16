# Session 2: OOP with Ruby

## Overview

Seperti yang telah disebutkan sebelumnya, Ruby merupakan bahasa pemrograman yang berorientasi objek. Semua yang bisa kita manipulasi di Ruby adalah sebuah objek. 

Di dalam pemrograman berorientasi objek, sebuah kelas memuat berbagai properti, seperti method dan variabel. Kelas bisa mewarisi properti dari kelas pendahulu (parent class) atau superclass nya, sehingga membentuk hierarki kelas dengan base class di tempat paling atas. Kelas paling atas (base class) di Ruby adalah `Object`. 

Sebuah kelas didefinisikan dengan keyword `class`, dan diakhiri dengan sebuah `end`.

```ruby
class Hello
  def initialize( name ) 
    @name = name
  end

  def hello_txt
    puts "Hello, " + @name + "!"
  end
end

hi = Hello.new("World")
hi.hello_txt # => Hello, World!
```

Method `initialize` pada Ruby merupakan constructor, yang otomatis akan dieksekusi pertama kali setelah objek kelas tersebut diciptakan. Pada contoh di atas, method `initialize` akan mendefinisikan sebuah instance variable `@name` dan meng-assign-nya dengan argumen yang dimasukkan.


## Instance Variables

Instance variabel adalah variabel yang ada di dalam instance sebuah kelas, dan cakupannya terbatas. Sebuah instance variable diawali dengan tanda `@`, seperti instance variable pada contoh sebelumnya `@name`. Kita bisa mendefinisikan sebuah instance variable di dalam atau di luar sebuah method. Namun, kita hanya bisa mengaksesnya dari luar objek dengan menggunakan method getter (accessor) dan setter.

```ruby
class Hello
  def initialize( name ) 
    @name = name
  end

  def hello_txt
    puts "Hello, " + @name + "!"
  end

  def name
    @name
  end

  def name=(value)
    @name = value
  end
end

hi = Hello.new("World")
hi.name # => World
hi.name = "CCBI"
hi.name # => CCBI
```

## Access Control


## Class Variables and Methods


## Inheritance

Tidak seperti C++ yang mendukung multiple inheritance, Ruby menggunakan single inheritance, yaitu sebuah kelas hanya bisa mewarisi properti dari 1 parent class. 


## Modules


## Scope


## Global Variables and Constants


## Formatted Textual Output

