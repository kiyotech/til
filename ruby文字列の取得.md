## 一行に一つなら
```
line = gets.chomp.to_s
puts line
```

---
## 一行に複数要素
```
line = gets.chomp.split(' ')
puts line
*('')中に半角スペース入れない場合
tokyo
line =gets.chomp.split('')
puts line
["t", "o", "k", "y", "o"]
```

---
## 複数行にひとつづつ文字列
```
lines = readlines.map(&:chomp)
puts lines
```

---
## 文字列の長さ
```
.length
```
---
## 文字を囲う. 
```
def frame_string(str)
  frame = "+" * (str.length + 2) 
  framed_str = "+" + str + "+"
  [frame, framed_str, frame].join("\n")
end

puts frame_string(gets.chomp)
```

---
## 文字列の配列を変換
```
S = gets.to_s
replace_pattern = {"A" => "4", "E" => "3", "G" => "6", "I" => "1", "O" => "0", "S" => "5", "Z" => "2"}
fixd_S = S.gsub(/A|E|G|I|O|S|Z/, replace_pattern)
puts fixd_S
```

---
## 文字列から指定の文字を削除
```
S = gets.to_s
puts S.delete!("aeiouAEIOU")
```

---
## 文字列を分割
```
str = "Border-Left is Red"
strAry = str.split(/[- ]/)
```

この場合「-」と「 」で分割している
["Border", "Left", "is", "Red"]となる

---
## 指定の文字の文字数を求める
```
 A = strAry[i].scan('<').length
```
 
---
## 置換
```
hidden_text = sample_text.gsub(/[a-z]/, "#")
p hidden_text # "T### ####### ## # ######."
```

---
## 文字列の指定の区間を抽出
a文字目からb文字分
```
line = gets.chomp.to_s
puts line[a - 1, b ]
```

---
## 文字列の頭文字を大文字
```
input = gets.chomp
puts input.upcase
```

---
## 文字列のaからb文字目までを大文字にする
```
str[a-1..b-1] = str[a-1..b-1].upcase
```

---
## 文字列に含まれる特定のもののかず
```
puts s.count(c)
```

---
## 文字列の要素を半角スペース開けて表示
```
str = gets.chomp
puts "#{str[0]} #{str[1]}"
```

---
## 配列の中の重複をなくす
```
array = ["HND", "NRT", "KIX", "NGO", "NGO"] 
new_array == array.uniq
puts new_array #=> ["HND", "NRT", "KIX", "NGO"] 
```

---
## 重複してる要素を抽出
```
array = ["HND", "NRT", "KIX", "NGO", "NGO", "NGO", "NGO", "NGO"]
puts array.select{ |e| array.count(e) > 1 }.uniq
```

---
## join は Ruby の文字列メソッドです。配列の要素を連結して1つの文字列にまとめます。引数に渡した文字列が区切り文字となります。
```
array = ["paiza", "paiza"]
puts array.join(" ")
```

---
## アルファベットの並びから特定のindex間の値を取得
```
alphabets = ("A".."Z").to_a
a = alphabets.index("#{f}")
b = alphabets.index("#{l}")
puts alphabets[a..b]
```

---
## 文字列を１文字ごと分解して二重配列の縦横を入れ替える
```
transposed = lines.map(&:chars).transpose.map(&:join)
```

---
## 文字列の配列から数値を選びそのインデックスを取得する
```ruby
s = gets.chomp.split('')
indexes = []
s.each_with_index do |element, index|
  if element.match(/\d/) # elementが数字である場合
    indexes << index # indexを追加する
  end
end
puts indexes.inspect
```
インデックス間の値をそれぞれ取得
```ruby
indexes.each_with_index do |start, i|
  (i...indexes.length).each do |j|
    last = indexes[j]
    puts s[start..last].join
  end
end
```

---
## length、size、count
https://qiita.com/motoki4917/items/ffc89d955e20b91d1014

---
## アルファベットの配列を作る
```ruby
array = ('a'..'z').to_a
p array
```
