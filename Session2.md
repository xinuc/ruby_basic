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

Instance variabel adalah variabel yang ada di dalam instance sebuah kelas, dan cakupannya terbatas. Sebuah instance variable diawali dengan tanda `@`, seperti instance variable pada contoh sebelumnya `@name`. Kita bisa mendefinisikan sebuah instance variable di dalam atau di luar sebuah method. Namun, kita hanya bisa mengaksesnya dari luar objek dengan menggunakan method accessor: getter dan setter.

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


## Accessors

Ruby menyederhanakan pembuatan getter dan setter secara meta-programming dari kelas `Module`, yakni menggunakan method `attr`, `attr_reader`, `attr_writer` dan `attr_accessor`.

Method `attr` akan membuat sebuah getter. Jika argumen keduanya `true`, ia juga akan membuat sebuah setter.

```ruby
class Bird
  attr :chirp, true
end

Bird.instance_methods - Object.instance_methods # => ["chirp","chirp="]

bird = Bird.new
bird.chirp = "Tweet!"
bird.chirp # =>  Tweet!
```

Method `attr_reader` akan menciptakan getter, sedangkan method `attr_writer` akan menciptakan setter.

```ruby
class Bird
  attr_reader :chirp # getter
  attr_writer :chirp # setter
end

Bird.instance_methods - Object.instance_methods # => ["chirp","chirp="]
```

Method `attr_accessor` akan memberikan efek yang sama seperti jika memanggil `attr_reader` dan `attr_writer`.

```ruby
class Bird
  attr_accessor :chirp, :fly, :spawn
end

Bird.instance_methods - Object.instance_methods # => [:chirp, :chirp=, :fly, :fly=, :spawn, :spawn=]
```


## Class Variables

Class variable merupakan variabel yang digunakan bersama oleh semua instance suatu kelas, mirip seperti konsep static variable di Java atau C++. Class variable di Ruby ditandai dengan `@@`.

```ruby
class Bird
  @@count = 0

  def initialize
    @@count += 1
  end

  def count
    @@count
  end
end

b1 = Bird.new
b2 = Bird.new
b3 = Bird.new
b1.count # => 3
```


## Class Methods

Class method (static method) merupakan method yang berasosiasi dengan kelas atau module di Ruby, bukan instance dari suatu kelas. Kita bisa mengeksekusi sebuah class method tanpa sebuah instance objek. Class method di Ruby selalu diawali dengan `self.`

```ruby
class Bird
  def self.tweet
    puts "Tweeeeet!!"
  end
end

Bird.tweet # => Tweeeeet!!
```

## Inheritance

Pewarisan (inheritance) pada Ruby dilakukan dengan menggunakan operator `<`.

```ruby
class Bird
  attr_accessor :chirp, :egg
end

class Duck < Bird
  attr_accessor :quack
end

d = Duck.new
put d.respond_to?(:egg) # => true
```

Jika kelas `Bird` di atas berada di file yang berbeda dengan kelas `Duck`, maka terlebih dulu kita perlu `require` file tersebut. Ruby akan mencari file tersebut berdasarkan `$LOAD_PATH` yang telah didefinisikan. 


## Modules

Tidak seperti C++ yang mendukung multiple inheritance, Ruby menggunakan single inheritance, yaitu sebuah kelas hanya bisa mewarisi properti dari 1 parent class


## Scope


## Global Variables and Constants


## Formatted Textual Output

