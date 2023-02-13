## 標準入力からの二次元配列の作り方（区切りが”,"の場合）
array = []
while line = gets
    line.chomp!
    array.push(line.split(","))
end
p enemy_img
---
count = gets.to_i
puts("データ個数 #{count}")

for i in 1..count
    line = gets
    puts "hello #{line}"
end
---
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
---
## 二次元配列の値の取得の仕方
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
---
## インデックスも表示する
landmap = Array.new(10).map{Array.new(20,"森")}
landmap.each_with_index do |line, i|
    print "#{i}:"
    line.each do |area|
        print area
    end
    puts ""
end
---
## 箱に入るボール
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
---
## 二次元配列の行列入れ替え
.transpose
