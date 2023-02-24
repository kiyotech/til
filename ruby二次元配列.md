## 任意の範囲の整数の配列
```ruby
arr = (-n..n).to_a
```
## 0を抜かす
```ruby
arr = (-n..n).to_a.reject {|i| i == 0}
```

---
## 標準入力からの二次元配列の作り方（区切りが”,"の場合）
```ruby
array = []
while line = gets
    line.chomp!
    array.push(line.split(","))
end
p enemy_img
```
```ruby
count = gets.to_i
puts("データ個数 #{count}")

for i in 1..count
    line = gets
    puts "hello #{line}"
end
```
```ruby
team = []
while line = gets
    line.chomp!
    team.push(line.split(","))
end
print "<table>"
team.each do |line|
    print "<tr>"
    line.each do |person|
        print "<td><img src='#{players_img[person.to_i]}'></td>"
    end
    puts "</tr>"
end
  puts "</table>"
```
数値を二次元配列へ
```ruby
3
1 2 3
4 5 6
7 8 9

n = gets.to_i
array = []
n.times do
    line = gets.split.map(&:to_i)
    array << line
end
p array
/ => [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
---
## 二次元配列の値の取得の仕方
```ruby
enemy_img = [[0,0,1,1,1,1,1,1,1,1,1,1,1,1,0,0],
             [1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1],
             [1,0,0,1,1,1,0,0,0,1,1,1,0,0,0,1],
             [1,1,0,0,0,0,1,1,0,0,0,0,0,0,1,1],
             [0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,0],
             [0,0,0,1,1,1,0,0,0,0,0,1,1,1,0,0],
             [0,0,0,0,1,1,1,0,0,0,0,0,0,1,1,1]]

enemy_img.each do |line|
    # p line
    line.each do |dot|
        # print dot
        if dot == 1
            print "#"
        else
            print " "
        end
    end
    puts ""
end
```

---
## インデックスも表示する
```ruby
landmap = Array.new(10).map{Array.new(20,"森")}
landmap.each_with_index do |line, i|
    print "#{i}:"
    line.each do |area|
        print area
    end
    puts ""
end
```

---
## 箱に入るボール
```ruby
input = gets.split.map(&:to_i)
n = input[0]
r = input[1]
array = []
n.times do 
  x = gets.split.map(&:to_i)
  array << x
end
array2 = []
array.each_with_index do |line, i|
    sum = 0
    line.each do |dot|
        if dot >= r * 2
            sum += 1
        end
    end
    if sum == 3
        array2 << i + 1
    end
end
puts array2.sort
```

---
## 二次元配列の行列入れ替え
```ruby
.transpose
```

---
## 二次元配列を一次元配列に戻す
```ruby
array.map(&:join)
```
もしくは
```ruby
array = [["S_1", "D_1"], ["S_2", "D_2"], ["S_3", "D_3"], ["S_4", "D_4"], ["S_5", "D_5"], ["S_6", "D_6"], ["S_7", "D_7"], ["S_8", "D_8"], ["S_9", "D_9"], ["S_10", "D_10"], ["S_11", "D_11"], ["S_12", "D_12"], ["S_13", "D_13"], ["H_1", "C_1"], ["H_2", "C_2"], ["H_3", "C_3"], ["H_4", "C_4"], ["H_5", "C_5"], ["H_6", "C_6"], ["H_7", "C_7"], ["H_8", "C_8"], ["H_9", "C_9"], ["H_10", "C_10"], ["H_11", "C_11"], ["H_12", "C_12"], ["H_13", "C_13"]]
flat_array = array.flatten

puts flat_array.inspect
#=> ["S_1", "D_1", "S_2", "D_2", "S_3", "D_3", "S_4", "D_4", "S_5", "D_5", "S_6", "D_6", "S_7", "D_7", "S_8", "D_8", "S_9", "D_9", "S_10", "D_10", "S_11", "D_11", "S_12", "D_12", "S_13", "D_13", "H_1", "C_1", "H_2", "C_2", "H_3", "C_3", "H_4", "C_4", "H_5", "C_5", "H_6", "C_6", "H_7", "C_7", "H_8", "C_8", "H_9", "C_9", "H_10", "C_10", "H_11", "C_11", "H_12", "C_12", "H_13", "C_13"]
```
---
## 五目並べの縦方向
```ruby
array = []
while line = gets
    line.chomp!
    array.push(line.split(""))
end
array2 = array.transpose
n = array2.length
(0...n).each do |i|
    array2[i] = array2[i].join
end
if array2.include?("OOOOO")
    puts "O"
elsif array2.include?("XXXXX")
    puts "X"
else
    puts "D"
end
```
---
## 五目並べの斜め
```ruby
array = []
while line = gets
    line.chomp!
    array.push(line.split(""))
end
n = array.length
array1 = []
array2 = []
(0...n).each do |i|
    array1 << array[i][i]
    array2 << array[i][n - 1 - i]
end
array1 = array1.join
array2 = array2.join
if array1 == "OOOOO" || array2 == "OOOOO"
    puts "O"
elsif array1 == "XXXXX" || array2 == "XXXXX"
    puts "X"
else
    puts "D"
end
```

---
## 文字列を１文字ごと分解して二重配列の縦横を入れ替える
```ruby
transposed = lines.map(&:chars).transpose.map(&:join)
```

---
## 二個の配列を交互に取り出した二次元配列にする
```ruby
shuffled = top.zip(bottom)
```

---
## カードのシャッフル
```ruby
K = gets.to_i
cards = []
suit = ["S","H","D","C"]
suit.each do |suit|
  (1..13).each do |num|
    cards << "#{suit}_#{num}"
  end
end
top = cards.slice(0, 26)
bottom = cards.slice(26, 52)
if K == 0
    puts cards
else
    flat_shuffled = []
    K.times do
        shuffled = top.zip(bottom)
        flat_shuffled = shuffled.flatten
        top = flat_shuffled.slice(0, 26)
        bottom = flat_shuffled.slice(26, 52)
    end
    puts flat_shuffled
end
```
