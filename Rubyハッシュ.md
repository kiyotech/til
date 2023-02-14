## キーで並び替えて、バリューの和を求める
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
