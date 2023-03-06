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
input = gets.split.map(&:to_i)
N = input[0]
X = input[1]
Y = input[2]
Z = input[3]
---
11
22
33
lines = readlines.map(&:to_i)
---
2
2 5
3 4
input_line = gets.to_i
input_line.times do
  X = gets.split.map(&:to_i)

end
```
---
## 数値をバラバラに配列へ収納
```ruby
line = gets.chomp.split('').map(&:to_i)
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
## 配列から５以上の数値だけ取って新しい配列を作る
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

