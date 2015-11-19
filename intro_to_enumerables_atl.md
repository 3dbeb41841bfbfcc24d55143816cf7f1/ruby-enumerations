##Enumerables - Opening Discussion/Hook
- What does Enumeration mean? Or how do I enumerate?
- Enumeration happens all the time in real life and code. For example, when Ashley introduced the instructors, she asked us each to tell a little bit about ourselves, so went one by one and introduced ourselves
- Think-Pair-Share: Write down 3 ways you enumerate over a list of things in every day life. Share them with your partner, giving an example story for each one.



##IWBAT...
- define Enumerable
- enumerate over arrays and hashes


##Connection to Long Term Goal
- Understand possibilities
- Use best practices as a developer (e.g.- DRY)
- Establish a solid foundation of skills
- Learn to think like a programmer


##Defining Enumerable

**How did we iterate over an array in JS?** It was pretty convoluted using a loop:

```js
for (var i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
};
```

**As Ruby developers**, we now see the world thru object-oriented eyes so that data structure would be an object (or, a collection... hashes or arrays), and we normally use a type of method called an **enumeration** on that object. 

__Enumerable__ - An enumeration is a collection of items that is a complete, ordered listing of all of the items in that collection. Hashes and arrays are enumerables. **Translation... a collection that you can loop through.**

We can do for loops in Ruby, too, but we've got something _much_ nicer:

```ruby
numbers.each do |number|
  puts "i am number #{number}"
end

# i am number 1
# i am number 2
# i am number 3
# i am number 4
# i am number 5

```

Isn't that just so incredibly readable?

<br>

##Code Along
**WE DO**

- Using loops, print out "I <3 " followed by the name of each tv show in the array in all caps:

```ruby
fav_shows = ["Girls", "Game of Thrones", "House of Cards", "The Bachelor", "Modern Family", "Mad Men"]

i = 0

while i < fav_shows.length
  puts "I <3 #{fav_shows[i].upcase}"
  i += 1
end
```


- Let's rewrite the above so that our code is DRY. Let's put it into a Ruby method: 

 
```ruby
def loop_and_print(shows)
  i = 0
  while i < shows.length
    puts "I <3 #{shows[i].upcase}"
    i += 1
  end
end

loop_and_print(fav_shows)
```


- Now let's use enumeration and `.each`

```ruby
# inline
fav_shows.each { |show| puts "I <3 #{show.upcase}" }

# or as a block
fav_shows.each do |show| 
    puts "I <3 #{show.upcase}"
end
```



`.each` doesn't mutate it's object, instead, it literally just performs some block of Ruby expressions some number of times, defined as the length of a collection, and upon each iteration it offers up 

__At it's heart, an enumeration is a loop that happens inside a data structure's object (a collection), instead of outside of it__

More enumerations: `.map`, `.join`, `.select`, `.reduce` (find the ruby-docs entry for Enumerable).

<br>

#### Extra Detail: Dem Blocks Tho!

That `do`/`end` thing you're messing with is called a _block_, and it just runs the code in between, almost like a little function without a name - like anonymous functions in JavaScript or lambdas in Python.

You'll see blocks all the time, and you'll use `.each` like it's your job. It just loops through each value in your array and assigns a local variable (that you decide) to each object. You come up with what you want it called in the "pipes", aka those tall neighbors surrounding the variable: `|a_variable_of_my_choosing|`.

To make it super clear: if `numbers` is a variable holding `[1,2,3,4,5]`, then `numbers.each` will go through each number and do _something_ to each variable. It's sort of as if the code is doing this:

```ruby
# numbers.each do |number|
#   puts "i am number #{number}"
# end

number = 1
puts "i am number #{number}"

number = 2
puts "i am number #{number}"

number = 3
puts "i am number #{number}"

number = 4
puts "i am number #{number}"

number = 5
puts "i am number #{number}"
```

Oh, and for best practice, always try to name`|a_variable_of_my_choosing|` the singular tense of the array you're iterating over: ```numbers.each do |number|``` or ```articles.each do |article|```

Of course, the beauty of loops is that we don't have to write all that out.

And a bonus tip: `do`/`end` is functionally the same as `{`/`}`, so you'll see both. The curly braces are for when you want to keep it on one line, but it does not matter.

```ruby
# totally the same
numbers.each do |number|
  puts "i am number #{number}"
end

# totally the same
numbers.each {|number| puts "i am number #{number}"}
```
<br>
### YOU DO - Arrays - Independent Practice (15 minutes)

Alright, practice time. Quick solo challenge, we'll be setting a timer for 10 minutes!

- Given the following list of student names, **iterate over them**, **prepending** "A+ " if their name includes an "A" in it. Make a new array if you need to
- Then, **sort the students** so that A+ students come first
- Next, **select just the students with A+** in their names. Look it up in the Ruby docs if you need to.
- Finally, **count how many A+ students you have**

```ruby
students = ['Suzy', 'Daniel', 'James', 'Mary', 'Phillip', 'Siegfried']
```


<br>
##More Enumeration over arrays and hashes

**I DO:**

- Live coding - `array.each`
	- Block
	- In-line

```ruby
primes = [2, 3, 5, 7]
primes.each do |n|
  puts “#{n} is prime.”
end

-OR-

primes.each { |n| puts “#{n} is prime.” }

```

- Live Coding - Hashes
	- Create an array of hashes of friends
	- Print out each one’s names, how I met each one
	- Create new array of just their names

```ruby
friends = [ { name: ‘Kristin’, met: ‘Atlanta’ }, { name: ‘Doug’, met: ‘School’ }, { name: ‘Kevin’, met: ‘Work’ }]

friends.each { |friend| puts “I met #{friend[:name]} in/at #{friend[:met]}” }

friends_name_only = []

friends.each do |friend|
  friends_name_only << friend[:name]
end

-OR-

friends_name_only = friends.map { |friend| friend[:name] }
```
<br>
###More Examples

We have already touched on blocks, if we've seen code like:

__blocks__

`10.times { |i| puts i, " " }`

...same as...

```ruby
10.times do |i|
  puts "i is #{i}"
end
```

__Iterating through Arrays__

```ruby
foods = ["carrots", "kale", "beets"]
foods.each do |vegetable|
    puts "i like #{vegetable}"
end
```

... is the same as ...

```ruby
for veg in ["carrots", "kale", "beets"] do
    puts "i like #{veg}"
end

# Will _each_ print out:
# >i like carrots
# >i like kale
# >i like beets
```

__Iterating through Hashes__

```ruby
car = {wheels: 4,doors: 2,seats: 5}
car.each do |key, num|
  puts "my car has #{num} #{key}"
end

# Will print out:
# my car has 4 wheels
# my car has 2 doors
# my car has 5 seats
```
	

A block is a portion of code that is passed to a method - in fact, blocks can be considered little methods of their own, just with no name
  
Used very often with "enumerable" objects (Arrays, Hashes) to run the block against each element in the collection.

For this lesson we will use some of the enumerable methods to demonstrate blocks. You will use these methods *all the time* in your Ruby programming career, so become very familar with them.

- Demonstrate googling for "ruby api array", "ruby api enumerable" - reinforce how importand it is to remember to do this, and to read this 

``` ruby
def print_name(name)
  puts name
end

names = %w(Fred Wilma Barney) 

for i in 0..names.size
  print_name(names[i])
end
  
  # size is an enumerable method for the 'size' of objects, length is for strings
```

  or...
  
```
%w(Fred Wilma Barney).each { |name| print_name(name) }
```

  or ...
  
```
%w(Fred Wilma Barney).each do |name| 
  print_name(name)
end
```

  - We generally use {} for one-line blocks, and "do..end" for multiline blocks

<br>
### Let's play with blocks:
  
```ruby
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
<br>
### Aside... if there's time, show the previous method refactored

```ruby
"The quick brown fox jumped over the lazy dog".split.each do |word|
   puts (if word.length.even?
     word.downcase
   else
     word.upcase
   end)
end
  
"The quick brown fox jumped over the lazy dog".split.each do |word|
   puts word.__send__(word.length.even? ? :downcase : :upcase)
end
```


**We do:**

- Pairs: Create an array of hashes, loop through and print a trait, also use map to return an altered array
- Walk through the following via docs, guess what will be returned
	- `array.select`
	- `array.each_index`
	- `hash.each_pair`
	- `hash.reject`

**You do:**

- Go through Ruby docs, get the following to work with your own examples. Do half block style and half in-line
	- `array.reject`
	- `array.each_with_index`
	- `hash.select`
	- `hash.delete_if`

<br>

##Closing

- Think-Pair-Share: What are 3 examples of enumeration in web apps that you use?
- Ask for each person’s top one (give a unique one if possible)

<br>

##Lab
- Do morning_enumeration_`lab`


###Bonus
- If you haven’t already, go back and do the previous bonuses
- Before we said to ignore each method that has a block. This restriction has been lifted. So go back to your `arrays.rb` and `hashes.rb` and do each method you didn’t do before.
