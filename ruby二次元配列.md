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
