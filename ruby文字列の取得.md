## 一行に一つなら
line = gets.chomp.to_s
puts line
---
## 一行に複数要素
line = gets.split(' ')
puts line
*('')中に半角スペース入れない場合
tokyo
line =gets.split('')
puts line
["t", "o", "k", "y", "o"]
---
## 複数行にひとつづつ文字列
lines = readlines.map(&:chomp)
puts line
---
## 文字列の長さ
.length
---
## 文字を囲う. 
def frame_string(str)
  frame = "+" * (str.length + 2) 
  framed_str = "+" + str + "+"
  [frame, framed_str, frame].join("\n")
end

puts frame_string(gets.chomp)
---
## 文字列の配列を変換
S = gets.to_s
replace_pattern = {"A" => "4", "E" => "3", "G" => "6", "I" => "1", "O" => "0", "S" => "5", "Z" => "2"}
fixd_S = S.gsub(/A|E|G|I|O|S|Z/, replace_pattern)
puts fixd_S

---
## 文字列から指定の文字を削除
S = gets.to_s
puts S.delete!("aeiouAEIOU")
---
## 文字列を分割
str = "Border-Left is Red"
strAry = str.split(/[- ]/)
この場合「-」と「 」で分割している
["Border", "Left", "is", "Red"]となる
---
## 指定の文字の数を求める
 A = strAry[i].scan('<').length
---
置換
hidden_text = sample_text.gsub(/[a-z]/, "#")
p hidden_text # "T### ####### ## # ######."
---
