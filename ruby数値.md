## 入力数値の取り出し方
```ruby
１１１
N = gets.to_i
小数点表示
.to_f
to_iメソッドが文字→数値
to_sメソッドが数値→文字
---
11 22 33 44
line = gets.split.map(&:to_i)
N = input[0]
X = input[1]
Y = input[2]
Z = input[3]
---
11
22
33
lines = readlines.map(&:to_i)
or
a = N.times.map{gets.chomp.to_i}
---
2
2 5
3 4
input_line = gets.to_i
array = []
input_line.times do
  array << gets.split.map(&:to_i)
end
```
---
## 半角スペースで区切られた数値をバラバラに配列へ収納
```ruby
line = gets.chomp.split(' ').map(&:to_i)
p line
```
---
### 配列の要素数を調べます。
### 中身が nil であれっても1要素と数えます。
### 配列がからであれば ゼロを返します。
```ruby
puts [1, 2, 3, 4, 5].size #=> 5
puts [1, 2, nil, nil, 5].size #=> 5
puts [].size #=> 0
puts [nil].size #=> 1
```

### 配列やハッシュ、範囲の場合は要素数を返します。
```ruby
puts [1, 2, 3, 4, 5].size #=> 5
puts ( {1 => 10, 2 => 20}.size ) #=> 2
puts (1..5).size #=> 5
```

### 文字列の場合は文字数を返します。
### 半角スペースも1文字として評価されます。
```ruby
puts "h e l l o ".size #=> 10
```

---
## 配列の積
```ruby
array = [1,2,3,4,6,8,10]
product = array.reduce(:*)
puts product
```

---
## 配列の要素の最大・最小
```ruby
array = [1,2,3,4,5]

min = array.min
max = array.max

puts min
puts max
```
## 最大値のインデックスを求める
```ruby
p a.index(a.max)
```
---
## 比較し最大最小を求める
```ruby
max = [x,y,z].max
min = [x,y,z].min
```
---
## 処理を止める
```ruby
break
```

---

## 配列の要素とインデックス両方取得する
```ruby
array.each_with_index do |num, i|
```

---
## 配列から５以上の数値だけ取って新しい配列を作る select
https://www.sejuku.net/blog/19226
```ruby
array = [4, 0, 5, -1, 3, 10, 6, -8]
new_array = array.select { |e| e >= 5 }
puts new_array.sum
```

---
## 配列の並び替え
昇順
```ruby
num = gets.split.map(&:to_i)
puts num.sort
```

（破壊的は）.sort!
降順
```ruby
p array.sort.reverse
array.sort!.reverse!
```

並び替える前のインデックスを保持したまま並び替え
```ruby
order_i = order.each_with_index.sort
```

---
## 数値と文字列の含まれる配列を数値で並び替える
```ruby
n = gets.to_i
list = []

n.times do
  char, num = gets.chomp.split
  list << [char, num.to_i]
end

list.sort_by { |char, num| num }.each do |char, num|
  puts char
end
```
## 割り算の小数点は切り捨て
切り上げたいなら
```
(分子.to_f / 分母).ceil
```
---
## 逆順
```ruby
a = [ "a", "b", "c" ]
a.reverse_each {|x| print x, " " }
# => c b a
```

---
## 配列の後半を切り出して前に持ってくる
```ruby

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 配列の最後の4つを切り出す
last_four = array.pop(4)

# last_fourを配列の先頭に結合
array = last_four + array

puts array.inspect # [7, 8, 9, 10, 1, 2, 3, 4, 5, 6]
```

---
## 文字列の配列を数値の配列へ
```ruby
integers = strings.map{|n| n.to_i}
```

---
## shift, unshift, pop, push
https://qiita.com/kaichan/items/a215684b539a0b355944

---
## 要素の挿入
```ruby
配列.insert(挿入位置, 挿入する要素)
```
---
## 要素の削除
https://qiita.com/hapiblog2020/items/6bdc2f6f2a0a0388ab89

---
## chunk_while 連続した部分をまとめる
https://docs.ruby-lang.org/ja/2.7.0/method/Enumerable/i/chunk_while.html

```ruby
n = gets.to_i
lines = readlines.map(&:to_i)
lines = lines.sort
arr = lines.chunk_while {|i, j| i+1 == j }.to_a
p arr
```

---
## 配列を半角スペース挟んで出力
```ruby
puts ans.join(" ")
```

---
## 配列を半角スペース区切りで出力
```ruby
# 文字列として出力している
array = []
for i in 1..9
    array << 8*i
end
puts array.join(" ")
```

---
## 十進数を二進数へ変換
```ruby
n = gets.to_i
binary = 0
i = 0
while n > 0
  digit_num = n % 2
  binary += digit_num * 10 ** i
  n /= 2
  i += 1
end
puts binary
```


---
## reduceメソッドは、配列や範囲などの要素を一つにまとめる役割を持ちます。引数には、要素をまとめる際の演算子や初期値を指定できます。
```ruby
puts (1..5).reduce(:+)
```
---
## 階乗
```ruby
N = gets.chomp.to_i

puts (1..N).reduce(:*)
```

---
## 数値の配列を重複なしで作る
```ruby
require 'set' # setライブラリを呼び出す
a = gets.split.map(&:to_i).to_set
```

---
## 配列にその数値があるか確認
```ruby
if array.include?(x)
  puts ,,,
```
---
## 既存の配列のコピーを先頭から順番に作っていく
```ruby
n = gets.to_i
a = gets.split.map(&:to_i)

array = [a[0]]
(1...n).each do |i|
    if array.include?(a[i])
        puts "Yes"
    else
        puts "No"
        array << a[i]
    end
end
```

---
## 2つの変数の入れ替え
```ruby
a = 10
b = 20
puts a  # =>10
puts b  # =>20

a, b = b, a
puts a  # =>20
puts b  # =>10
```
---
## 配列のの総当たりの掛け算
```ruby
n = gets.to_i
a = n.times.map { gets.to_i }

n.times do |i|
    i.times do |j|
        puts a[i] * a[j]
    end
end
```
---
## 偶数奇数判定
```ruby
a.eve?
a.odd?
```
---
## 曜日判定
```ruby
n = gets.to_i
week = ["Sat", "Sun", "Mon", "Tue", "Wed", "Thu", "Fri"]

puts week[n % 7]

```
---
## 桁数は文字列に変換したら楽
```ruby
n = gets.chomp
puts n.length
```
---
## 整数n以下の数字で素数の数
```ruby
n = gets.to_i

ans = 0
(2..n).each do |i|
    is_prime = true
    (2..Math.sqrt(i).floor).each do |j|
        if i % j == 0
            is_prime = false
            break
        end
    end
    ans += 1 if is_prime
end

puts ans
```
### ライブラリを使う場合
```ruby
n = gets.to_i
count = 0
require 'prime'
(2..n).each do |v, i|
    if v.prime? 
        count += 1
    end
end
puts count
```
