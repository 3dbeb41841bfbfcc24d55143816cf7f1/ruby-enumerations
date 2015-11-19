##Enumerable Exercises

### #1 - Enumerable Examples

Go through each example and explain what is happening:

```
%w(Fred Wilma Barney).map { |name| name.reverse }

%w(Fred Wilma Barney).each { |name| puts name*3 }
  
(1..100).each { |i| puts i if i % 7 == 0 }    

%w(Fred Wilma Barney).each_with_index { |name, index| puts "#{name} is #{index.odd? ? "boys'" : "girls'"} name"}
      
(1..10).each_slice(3) { |a| puts a }    
  
(1..3).cycle(3) { |i| puts i }    
  
(1..10).select { |i| i.even? }    
  
(1..10).detect { |i| i.even? }    
  
(1..10).group_by { |i| i%3 }    

# Hashes are enumerable too
{name: 'GA WDI!', students: 13, location: 'Atlanta'}.each_pair do |k, v|
  puts "key '#{k}' has the value '#{v}'"
end

"The quick brown fox jumped over the lazy dog".split.each do |word|
   if word.length.even?
     puts word.downcase
   else
     puts word.upcase
   end
end

```

### #2 - Wine Cellar

- Here is an array containing some wines:

```
wine_cellar = [
  {:label => "Rutherford Hill", :type => "Chardonnay", :color => "white"},
  {:label => "Nina Veneto", :type => "Pinot Grigio", :color => "white"},
  {:label => "Wairau River", :type => "Sauvignon Blanc", :color => "white"},
  {:label => "Tangley Oaks", :type => "Merlot", :color => "red"},
  {:label => "Chimney Rock", :type => "Cabernet Sauvignon", :color => "red"},
  {:label => "Sanford", :type => "Pinot Noir", :color => "red"},
  {:label => "Alderbrook", :type => "Pinot Noir", :color => "red"},
  {:label => "Colavita", :type => "Pinot Noir", :color => "red"},
  {:label => "Markham", :type => "Chardonnay", :color => "white"},
  {:label => "Angeline", :type => "Pinot Noir", :color => "red"}
]

```


Write code that:
  
  - Adds a wine of your choice to the cellar
  - Returns a random wine from the cellar
  - Returns an array of just the white wines
  - Returns an array listing the unique types of wine
  - Returns an array with the all the wines that have 2-word labels
  - Returns an array with the labels of the wines that a type of Pinot Noir



### #3 - Students

```

students = ["Adam Barrett", "Jacob Cain", "Mikael Davis", "Salil Doshi", "Jonathan Eva", "Elaine Fang", "Parker Hart", "Richard Hessler", "Mary Hipp", "Inhak Kim", "Yi-Hsiao Liu", "Randy Latz", "Alexi Phillipson", "Matt Rundo", "Gabe Snyder", "Stephen Stanwood", "Joella Straley", "Brett Wallace", "Thomas Weaver"]
```

- Write code that:
  - Prints a random student
  - Prints the index of "Randy Latz"
  - Prints the fifth person (In this case it's Jonathan)
  - Prints a list of all the student names on one line, with each name separated by a pipe: |
  - Prints a list of the all of the last names
  - Prints the full names of all of the students with M names (Mikael, Mary, Matt)


### #4 - Starting a band

```
people = [
  {:name => "Peter", :money => 5, :plays_instrument => true},
  {:name => "Greg", :money => 10, :plays_instrument => false},
  {:name => "Travis", :money => 80, :plays_instrument => true},
  {:name => "Yi-Hsiao", :money => 20, :plays_instrument => false},
  {:name => "Parker", :money => 20, :plays_instrument => false},
  {:name => "Jake", :money => 90, :plays_instrument => false},
  {:name => "Matt", :money => 10, :plays_instrument => true},
  {:name => "Mary", :money => 15, :plays_instrument => false},
  {:name => "Alexi", :money => 8, :plays_instrument => false},
  {:name => "Salil", :money => 7, :plays_instrument => true},
  {:name => "Stephen", :money => 35, :plays_instrument => true},
  {:name => "Adam", :money => 12, :plays_instrument => true},
  {:name => "Joella", :money => 75, :plays_instrument => false}
]
```

* Who has the most money?
* If we have at least 5 people that play instruments we can start a band. Can we?
* If a new drum set costs $350, do we have enough money to buy one?
