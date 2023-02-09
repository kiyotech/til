入力数値の取り出し方
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
  s = gets.chomp.split(" ")
  print "hello = #{ s[0] } , world = #{ s[1] }\n"
end
---
# 配列の要素数を調べます。
# 中身が nil であれっても1要素と数えます。
# 配列がからであれば ゼロを返します。
puts [1, 2, 3, 4, 5].size #=> 5
puts [1, 2, nil, nil, 5].size #=> 5
puts [].size #=> 0
puts [nil].size #=> 1
# 配列やハッシュ、範囲の場合は要素数を返します。
puts [1, 2, 3, 4, 5].size #=> 5
puts ( {1 => 10, 2 => 20}.size ) #=> 2
puts (1..5).size #=> 5
# 文字列の場合は文字数を返します。
# 半角スペースも1文字として評価されます。
puts "h e l l o ".size #=> 10
---

---
array = [1,2,3,4,5]

min = array.min
max = array.max

puts min
puts max
---
文字列から指定の文字を削除
S = gets.to_s
puts S.delete!("aeiouAEIOU")
---
文字列を分割
str = "Border-Left is Red"
strAry = str.split(/[- ]/)
この場合「-」と「 」で分割している
["Border", "Left", "is", "Red"]となる
---
指定の文字の数を求める
    A = strAry[i].scan('<').length
---
置換
hidden_text = sample_text.gsub(/[a-z]/, "#")
p hidden_text # "T### ####### ## # ######."
---
処理を止める
break
---
配列の積
array = [1,2,3,4,6,8,10]
product = array.reduce(:*)
puts product
