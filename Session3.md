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
## Classes as Objects
## Metaprogramming
## IO
