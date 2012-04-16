# Sesi 2: Pemrograman Berorientasi Objek dengan Ruby

## Pendahuluan

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


## Access Control


## Class Variables and Methods


## Inheritance

Tidak seperti C++ yang mendukung multiple inheritance, Ruby menggunakan single inheritance, yaitu sebuah kelas hanya bisa mewarisi properti dari 1 parent class. 


## Modules


## Scope


## Global Variables and Constants


## Formatted Textual Output

