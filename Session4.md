# Session 4: Libraries & Testing

## Libraries

Salah satu keunggulan ruby adalah ruby memiliki banyak sekali library
yang bisa kita pakai sesuai kebutuhan kita.
Standar distribusi library di ruby adalah dengan menggunakan format yang
bernama *gem*.

### Instalasi & menggunakan gems

Sebuah gem adalah suatu kumpulan file library beserta metadatanya yang
dikompresi dengan gzip, biasanya dengan ekstensi `.gem`.
Untuk menginstall suatu library menggunakan gem, kita menggunakan
perintah

```
  $ gem install <nama gem>
```

contoh, kita akan menginstall builder, library untuk membuat dokumen xml:

```
  $ gem install builder
```

Untuk menggunakan library, baik yang bawaan ruby maupun yang diinstall
menggunakan gem, kita menggunakan method `require "<nama file>"`.

```ruby
require "rubygems" # tidak dibutuhkan untuk ruby 1.9 ke atas
require "builder"

xml = Builder::XmlMarkup.new(STDOUT, 2)
xml.person do
  name("Slamet Riyadi")
  location("Indonesia")
end
```

### RubyGems & Bundler

Pada umumnya, library ruby opensource dipublish oleh penulisnya ke rubygems.org,
sehingga siapapun dapat menginstall dan menggunakannya dengan mudah.


### Packaging Programs and Libraries for Distribution


## Testing

Testing merupakan aspek yang sangat penting dalam programming. Testing dapat
digunakan untuk memastikan apakah kode yang kita tulis bekerja sesuai dengan
yang kita harapkan.

Di ruby, ada banyak sekali testing framework yang tersedia.
Diantaranya: test-unit, minitest, rspec, shoulda dan lain-lain.
Pada sesi ini, kita akan membahas unit testing dengan menggunakan minitest,
yang merupakan test framework bawaan ruby (>= 1.9).

### Unit Testing with Minitest

Untuk menggunakan minitest, kita cukup me-require library tersebut dengan
`require 'minitest/autorun'` dan membuat testcase untuk mengetes kode yang
kita buat dengan assertion.

```ruby
  # person.rb
  class Person
    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end

    def fullname
      @first_name + " " + @last_name
    end
  end
```

```ruby
  # person_test.rb
  require './person'
  require 'minitest/autorun'

  class PersonTest < MiniTest::Unit::TestCase
    def setup
      @person = Person.new "John", "Smith"
    end

    def test_create_a_correct_fullname
      assert_equal "John Smith", @person.fullname
    end
  end
```

atau kita dapat menuliskan test dengan gaya rspec:

```ruby
  # person_test.rb
  require './person'
  require 'minitest/autorun'

  describe Person do
    before do
      @person = Person.new "John", "Smith"
    end

    it "should create a correct fullname" do
      @person.fullname.must_equal "John Smith"
    end
  end
```

kemudian kita jalankan dengan `ruby person_test.rb`, yang akan
menghasilkan

```
Run options: --seed 6446

# Running tests:

.

Finished tests in 0.000741s, 1349.7900 tests/s, 1349.7900 assertions/s.

1 tests, 1 assertions, 0 failures, 0 errors, 0 skips
```

yang berarti bahwa ada 1 test yang dijalankan tanpa failure.

### Introduction to TDD

TDD (test driven development) adalah metode pembuatan software dengan menuliskan test
terlebih dahulu, baru kemudian menulis kode implementasinya. Setelah kode implementasi
memenuhi testnya, kode kemudian di refactor ke dalam bentuk yang lebih modular.

Misalnya kita akan menulis kode untuk mengubah besaran temperatur dari celsius ke fahrenheit
dan sebaliknya. Pertama, kita akan membuat list fitur dari kode tersebut, yaitu:

* dapat mengubah temperatur dari celsius ke fahrenheit
* dapat mengubah temperatur dari fahrenheit ke celsius

kemudian, kita buat test case nya terlebih dahulu, sebagai berikut:

```ruby
  # temperature_converter_test.rb

  require 'minitest/autorun'

  describe TemperatureConverter do
    it "can convert temperature from celsius to fahrenheit" do
      TemperatureConverter.new(10).celsius_to_fahrenheit.must_equal 50
    end

    it "can convert temperature from fahrenheit to celsius" do
      TemperatureConverter.new(50).fahrenheit_to_celsius.must_equal 10
    end
  end
```

Jika kita jalankan test ini, maka tentu akan gagal. Baru kemudian kita buat implementasinya
sampai testnya berhasil.

```ruby
  # temperature_converter.rb

  class TemperatureConverter
    def initialize(temp)
      @temp = temp
    end

    def celsius_to_fahrenheit
      @temp * 9 / 5 + 32
    end

    def fahrenheit_to_celsius
      (@temp - 32) * 5 / 9
    end
  end
```
