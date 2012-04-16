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

### Lambda


## Classes as Objects
## Metaprogramming
## IO
