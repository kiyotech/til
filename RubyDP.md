## 漸化式
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

---
## フィボナッチ数列

整数 k が与えられます。
次のように定められた数列の k 項目の値を出力してください。
ちなみに、これはフィボナッチ数列と呼ばれる有名な数列です。

・ a_1 = 1 
・ a_2 = 1 
・ a_n = a_{n-2} + a_{n-1} (n ≧ 3)
```ruby
a_1 = 1 
a_2 = 1
a_3 = a_1 + a_2
a_4 = a_2 + a_3
a_n = a_{n-2} + a_{n-1} (n ≧ 3)
```
```ruby
k = gets.to_i

a = [1] * (k + 1)
(2..k + 1).each do |i|
    a[i] = a[i - 2] + a[i - 1]
end
p a[k - 1]
```
---

整数 n が与えられます。
階段を上るのに、1 歩で 1 段または 2 段を上ることができるとき、n 段の階段を上る方法は何通りあるでしょうか。
一段はd_1 二段はd_2
```ruby
a_0 = 1 通り。0段目、何もしないから一通り
a_1 = 1
a_2 = a_0 + a_1
a_3 = a_1 + a_2
a_4 = a_2 + a_3
a[n] = a[n-1] + a[n-2] (n >= 2)
```
```ruby
n = gets.to_i
a = [1]*(n+1)
for i in 2..n
    a[i] = a[i-1] + a[i-2]
end
puts a[n]
```
登る段数も変わる時
```ruby
n, a, b =gets.split.map(&:to_i)
dp = [0]*(n+1)
dp[0] = 1

for i in 1..n
    dp[i] = dp[i] + dp[i - a] if i >= a
    dp[i] = dp[i] + dp[i - b] if i >= b
end

puts dp[n]
```
八百屋にて、りんご1個が a 円で、りんご2個が b 円で売られています。

りんごの買い方を工夫したとき、n 個のりんごを手に入れるために必要な金額の最小値はいくらでしょうか。なお、買い方を工夫した結果、買ったりんごが n+1 個以上になってもよいものとします。
```ruby
a_1 = a
a_2 = a_1 + a or b 
a_3 = a_2 + a or a_1 + b
a_4 = a_3 + a or a_2 + b

a[n] = (a[n-1] + a, a[n-2] + b).min
```
```ruby
n, a, b = gets.split.map(&:to_i)
dp = [0]*(n + 1)
dp[1] = a
for i in 2..n
    dp[i] = [dp[i-1] + a, dp[i-2] + b].min
end
p dp[n]
```
```ruby
八百屋にて、りんご2個が a 円で、りんご5個が b 円で売られています。
りんごの買い方を工夫したとき、n 個のりんごを手に入れるために必要な金額の最小値はいくらでしょうか。なお、買い方を工夫した結果、買ったりんごが n+1 個以上になってもよいものとします。
n, a, b = gets.chomp.split.map(&:to_i)

dp = Array.new(n + 5, Float::INFINITY)

dp[0] = 0
dp[1] = a

(2..n+4).each do |i|
    dp[i] = [dp[i], dp[i - 2] + a].min if i >= 2
    dp[i] = [dp[i], dp[i - 5] + b].min if i >= 5
end

puts dp[n..].min
```
```ruby
n, x, a, y, b = gets.split.map(&:to_i)
dp = Array.new(n + 1000, Float::INFINITY)

dp[0] = 0
dp[1] = a

(2..n+999).each do |i|
    dp[i] = [dp[i], dp[i - x] + a].min if i >= x
    dp[i] = [dp[i], dp[i - y] + b].min if i >= y
end

puts dp[n..].min
```
---
## 最長増加連続部分列
n 人が横一列に並んでいます。左から i 番目の人を人 i と呼ぶことにします。人 i の身長は a_i [cm]です。
人 l ,人 l+1, ... , 人 r からなる区間 [l, r] について、すべての l ≦ i < r に対して a_i ≦ a_{i+1} が成り立っているとき、区間 [l, r] は背の順であると呼ぶことにします。また、区間 [l, r] の長さを r-l+1 とします。
背の順であるような区間のうち、最長であるものの長さを出力してください。
https://paiza.jp/works/mondai/dp_primer/dp_primer_lis_continuous_step0?language_uid=ruby
```ruby
n = gets.to_i
a = []
n.times { a << gets.to_i }

dp = Array.new(n, 1)

(1...n).each do |i|
    if a[i - 1] <= a[i]
        dp[i] = dp[i - 1] + 1
    else
        dp[i] = 1
    end
end

puts dp.max
```
---
## 最長部分増加列
```ruby
n = gets.to_i
a = n.times.map { gets.to_i }

dp = [1] * n
for i in 1...n
    for j in 0...i
        if a[j] < a[i]
            dp[i] = [dp[i], dp[j] + 1].max
        end
    end
end

puts dp.max
```
