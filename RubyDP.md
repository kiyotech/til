整数 x, d_1, d_2, k が与えられます。
次のように定められた数列の k 項目の値を出力してください。

・ a_1 = x 
・ a_n = a_{n-1} + d_1 (n が奇数のとき、n ≧ 3) 
・ a_n = a_{n-1} + d_2 (n が偶数のとき)

```ruby
a_1 = x                 a_2 = x + d_2
a_3 = x + d_2 + d_1     a_4 = x + d_2*2 + d_1
a_5 = x + d_2*2 + d_1*2 a_6 = x + d_2*3 + d_1*2
a_7 = x + d_2*3 + d_1*3
```
```ruby
x, d_1, d_2, k = gets.split.map(&:to_i)

a = [x]*(k + 1)
a[1] = x + d_2
(2..k + 1).each do |i|
    a[i] = a[i - 2] + d_1 + d_2
end

puts a[k - 1]
```
もしくは
```ruby
a = [x]*(k + 1)
(1..k + 1).each do |i|
    if i % 2 == 0
        a[i] = a[i - 1] + d_1
    else
        a[i] = a[i - 1] + d_2
    end
end

puts a[k - 1]
```
