## Rubyライブライ一覧　・公式リファレンス
https://docs.ruby-lang.org/ja/latest/library/index.html

## set
https://docs.ruby-lang.org/ja/latest/library/set.html
数値用の集合のライブラリなので、重複がない
```ruby
require 'set'

n, b = gets.split.map(&:to_i)
a = gets.split.map(&:to_i).to_set

if a.include?(b)
    puts 'Yes'
else
    puts 'No'
end
```
```ruby
require 'set'

n, b = gets.split.map(&:to_i)
a = gets.split.map(&:to_i).to_set

puts a.to_a # to_aでarrayに変換できる
```
