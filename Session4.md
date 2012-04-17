# Session 4: Libraries & Testing

## Libraries

## Leveraging Libraries
## RubyGems & Bundler
## Packaging Programs and Libraries for Distribution


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

kemudian kita jalankan dengan `ruby person_test.rb`.

## Introduction to TDD
## Red-Green-Refactor
## Describing a feature
## Verifying expectations
## Mocks & Stubs
