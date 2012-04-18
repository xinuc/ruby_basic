# Quiz

## Tuliskan output dari kode berikut:
  1. ```ruby
       1 + '0'
     ```

  2. ```ruby
       puts "i love ruby" =~ /ruby/
     ```

  3. ```ruby
       a = {
         :x => 20,
         :y => 70
       }
       b = {
         :y => 100,
         :z => 35
       }
       c = {:j => 30, :k => 45}

       puts a.merge(b)[:y] + c.delete(:k)
     ```

  4. ```ruby
       class ABC
         def initialize
           x = 0
         end

         def y
           x + 1
         end
       end

       a = ABC.new
       puts a.y
     ```

  5. ```ruby
       module A
         def x
           puts "Ax"
         end

         def y
           puts "Ay"
         end
       end

       module B
         def y
           puts "By"
         end

         def z
           puts "Bz"
         end
       end

       module C
         def x
           puts "Cy"
         end

         def z
           puts "Cz"
         end
       end

       class D
         include A
         include B
         include C

         def x
           puts "Dx"
         end
       end

       d = D.new
       d.x
       d.y
       d.z
     ```

  6. ```ruby
       @a = 10

       def m
         return 1 if @a > 4
         2
       rescue
         3
       end

       puts m
     ```

  7. ```ruby
       def x(y)
         if block_given?
           y + 3
         else
           5
         end
       end

       z = x 5 do |c|
         c + 5
       end

       puts z
     ```

  8. ```ruby
       class String
         def upcase
           "omg"
         end
       end

       puts "hello".upcase!
     ```

  9. ```ruby
       module M
         def method_missing(*args)
           "M"
         end
       end

       class C
         include M

         def n
           "N"
         end
       end

       c = C.new
       puts c.n + c.m
     ```

## Berapa jumlah failed test yang terjadi:

  10. ```ruby
        require 'minitest/autorun'

        class A
          def x
            "X"
          end

          def y
            5
          end

          def z
            raise "Z"
          end
        end

        describe A do
          before do
            @a = A.new
          end

          it "should do x" do
            @a.x.must_equal "X"
          end

          it "should do y" do
            @a.y.wont_be_nil
          end

          it "should do z" do
            @a.z.must_equal "Z"
          end
        end
      ```
