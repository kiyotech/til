## 要素を取得してハッシュへ収める
```
7
A 1
D 6
C 2
G 4
B 70
A 10
B 5
```
```
n = gets.to_i
h = {}
n.times do
  s, v = gets.split
  h[s] = v
end
p h
```

---
## ハッシュを出力
```
h.each do |key, v|
    puts "#{key} #{v}"
end
```

---
## 特定のキーのバリューを出力
```
s = gets.chomp.to_s
n = gets.to_i
h = {}
n.times do
  i, v = gets.split
  h[i] = v
end
h.each do |key, v|
    if key == s
    puts "#{key} #{v}"
    end
end
```

---
## キーで並び替えて、バリューの和を求める
```
7
A 1
D 6
C 2
G 4
B 70
A 10
B 5

n = gets.to_i
h = {}
n.times do
  s, v = gets.split
  v = v.to_i
  if h.key?(s)
    h[s] += v
  else
    h[s] = v
  end
end

h.sort_by { |_, v| -v }.each do |s, v|
  puts "#{s} #{v}"
end
```

---
## 占い
```
n = gets.to_i
hash1 = {}
n.times do
  name, blood = gets.split
  hash1[name] = blood
end
m = gets.to_i
hash2 = {}
m.times do
  blood, ans = gets.split
  hash2[blood] = ans
end
hash1.each do |name, blood|
    if hash2.key?(blood)
        puts "#{name} #{hash2[blood]}"
    end
end
```

---
## 配列を配列でeachしたいときはハッシュを使おう
```ruby
n, q = gets.split.map(&:to_i)

h = {}
n.times do |i|
    s = gets.chomp
    if h.key?(s)
        next
    else
        h[s] = i + 1
    end
end

q.times do
    t = gets.chomp
    if h.key?(t)
        puts h[t]
    else
        puts "-1"
    end
end
```
---
## ハッシュにこのキーが含まれていいるか確認する場合h.key?()
```ruby
n, m = gets.split.map(&:to_i)
h = {}
n.times do
    a, b = gets.chomp.split(' ')
    h[a] = b
end
m.times do
    c = gets.chomp
    if h.key?(c)
        puts h[c]
    else
        puts "-1"
    end

end
```
