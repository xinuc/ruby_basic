# Session 3: Advanced Topic

## Exceptions

Exception terjadi ketika aliran program terinterupsi karena error. Penanganan exception pada Ruby mirip dengan C++ dan Java.

|     C++    |     Java    |     Ruby     |
|:----------:|:-----------:|:------------:|
| try {}     | try{}       | begin/end    |
| catch {}   | catch {}    | rescue       |
|            | finally     | ensure       |
| throw      | throw       | raise        |


Ketika terjadi error, baris selanjutnya tidak akan dieksekusi. Ruby akan menangkap error tersebut dengan `rescue`, dan akhirnya menjalankan instruksi `ensure`.

```ruby
def foo
  str = "Hello world"
  str.bar
  puts "This line is ignored"
rescue NoMethodError => e
  print "Catching: " + e.to_s
rescue Exception
  print "Problem found!"
ensure
  puts " -- This is it"
end

foo # => Catching: undefined method `bar' for "Hello world":String -- This is it
```

Kita bisa melemparkan exception kapan saja dengan `raise`.

```ruby
def goo(n)
  if n < 0
    raise StandardError, "Negative number"
  else
    puts "It's positive"
  end
end

def hoo
  goo(-1)
  puts "It is printed?"
rescue Exception => e
  print "Exception: " + e.to_s
end

hoo # => Exception: Negative number
```

Selain menggunakan keyword `rescue` dan `raise`, kita bisa juga menggunakan method `catch` dan `throw` pada Ruby. Penggunaan argumen `catch` dan `throw` pada Ruby ini berbeda dengan di Java, meskipun namanya sama. 

```ruby
def print_me(n)
  puts n
  throw :done if n <= 0
  print_me(n-1)
end

catch(:done) do
  print_me(5)
end
```

## Advanced Blocks

Salah satu fitur yang paling diunggulkan Ruby adalah *closure* (fungsi tanpa nama). *Closure* itu seperti *method* di dalam *method* lainnya, yang mengacu atau berbagai *non-local variables*. *Closure* pada Ruby diimplementasikan dengan *block*, *proc* dan *lambda*.

### Block

Di Ruby, *block* biasanya diapit oleh kurung kurawal `{ }`, atau dengan `do/end`.

```ruby
days = [ "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" ]

days.each do |element|
  puts element
end

days.each { |e| puts e }
```

#### Yield

Pernyataan `yield` akan mengeksekusi *block* yang berasosiasi dengan suatu *method*.

```ruby
def foo
  if block_given?
    yield
    yield
  else
    puts 'No block here'
  end
end

foo { print 'Hello ' } # => Hello Hello

foo # => No block here
```

### Proc

Ruby memungkinkan kita menyimpan *procedure* atau `Proc` sebagai objek lengkap dengan konteksnya.

Penggunaan *block* pada Ruby itu relatif sederhana. Meskipun demikian, kita mungkin perlu punya beberapa *block* yang berbeda dan menggunakannya berkali-kali. Untuk menghindari kode yang repetitif tersebut, kita bisa menyimpannya sebagai *procedure* atau `Proc`, sebagai objek yang lengkap dengan konteksnya. Perbedaan antara *block* dan `Proc` adalah *block* merupakan suatu `Proc` yang tidak bisa disimpan dan merupakan solusi sekali pakai. 

```ruby
def foo
  count = Proc.new do
    [1,2,3,4,5].each do |i| 
      print i 
    end
  end

  count.call
  print " - " 
  count.call
  puts
end

foo # => 12345 - 12345
```


### Lambda

Di Ruby, *lambda* merupakan suatu *method* yang menciptakan objek *Proc* yang terkait dengan konteks saat ini dan melakukan pengecekan parameter ketika dipanggil.

Berbeda dengan Proc, lambda akan mengecek jumlah argumen yang dioper. 

```ruby
def foo(code)
  one, two = 1, 2
  code.call(one, two)
end

foo(Proc.new { |a, b, c| puts "a = #{a}, b = #{b}, c = #{c.class}" } ) # => a = 1, b = 2, c = NilClass

foo(lambda { |a, b, c| puts "a = #{a}, b = #{b}, c = #{c.class}" } ) # => ArgumentError: wrong number of arguments (2 for 3)
```


## Classes as Objects

*Object* merupakan *root* dari hierarki kelas di Ruby. Semua *method* dari kelas *Object* akan tersedia di seluruh kelas kecuali di-*override* secara eksplisit. Selengkapnya ada di http://www.ruby-doc.org/core/classes/Object.html


## Metaprogramming

*Metaprogramming* merupakan pemrograman yang memanipulasi program lainnya atau bahkan dirinya sendiri, atau mengerjakan hal-hal yang biasanya dilakukan pada *compile time*, pada waktu *runtime*. Kemampuan suatu objek untuk memanipulasi dirinya sendiri ini sering disebut sebagai *reflection*.

### Monkey Patching

Salah satu bentuk *metaprogramming* adalah *monkey patching*, yaitu memodifikasi *runtime code* dari suatu bahasa yang dinamis tanpa mengubah *source code* aslinya. 

```ruby
class Array
  def foo
    puts "Monkey patched!"
  end
end

[ 1, 2, 3, 4, 5 ].foo # => Monkey patched!
```


## IO
