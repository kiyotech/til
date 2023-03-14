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
