# Day 5: Big O Review Quiz

1. Mult choice

When calculating Big O, we calculate for the worst case, focus on the weakest link, and drop the coefficients.

- True
  - Yes! Big O cares about what will happen in the worst case scenario and simplifies its notation by dropping coefficients.
- False
  - Not quite. Which part do you think is not true?
- I don't know.
  - Don't worry. With time and practice, it'll start to sink in.

2. Mult choice

What is the difference between calculating time complexity versus space complexity for recursive procedures?

- Time complexity compares the input size to the total number of stack frames over time. Space complexity compares the largest number of frames that will be on the stack in one moment of time to the input size.
  - Correct! Time complexity is interested in all of the stack frames, while space complexity asks how deep will it go?
- Space complexity compares the input size to the total number of stack frames over time. Time complexity compares the largest number of frames that will be on the stack in one moment of time to the input size.
  - Not quite. Think about it this way: if you want to know how long it takes to get somewhere, you need to count up all of the minutes it takes to get there. If you're picking up and dropping off passengers along the way, you need to think about the largest number of passengers that will be in your car at any time, rather than the total number of passengers during the whole trip, to determine who you can pick up when.
- There is no difference. They are both calculated in the same way.
  - Not quite. There is a difference. You may wish to study some more.
- I don't know.
  - Don't worry. With time and practice, it'll start to sink in.

3. Mult choice

Logarithmic time O(log n) is slower than linear time O(n).

- False
  - Correct! Logarithmic time is faster than linear time.
- True
  - Not quite. Keep in mind that an algorithm might be logarithmic if it operates on subsets of the input, e.g. the input is divided on each operation, therefore reducing the total amount of work to be done.
- I don't know.
  - Don't worry. With time and practice, it'll start to sink in.

4. Mult choice

Calculate the time and space complexity for the following code. We've included both JS and Ruby for the same function.

<h3>JavaScript</h3>
<pre>
<code>
function bigSum(arr) {
	let total = 0;
  
  function add(depth = 0) {
  	if (depth === 2) {
    	return;
    }
    
    arr.forEach(num => {
    	total += num;
      add(depth + 1);
    });
  }
  
  add();
  
  return total;
}
</code>
</pre>

<h3>Ruby</h3>
<pre>
<code>
def big_sum(arr, depth = 0, total = 0)
  return total if (depth == 2)

  arr.each do |num|
    total += num
    total = big_sum(arr, depth + 1, total)
  end

  total
end
</code>
</pre>

- Time: O(n<sup>2</sup>), Space: O(n)
  - Correct! This code is similar to a loop within a loop where iterating over one element results in iterating over all of the elements again. This means it runs in quadratic time since the number of stack frames will equal the size of the input squared. The space is linear because the number of frames on the stack when it's at its deepest is proportional to the input size: specifically there will be `n` frames on the stack at the deepest layer.
- Time: O(n<sup>2</sup>), Space: O(n<sup>2</sup>)
  - Not quite. This code is similar to a loop within a loop where iterating over one element results in iterating over all of the elements again. This means it runs in quadratic time since the number of stack frames will equal the size of the input squared. However, the space required is not quadratic. What is the largest number of frames that will be on the stack if the array has 2 elements versus 3 elements. Remember, frames get popped from the stack as recursive methods start returning.
- Time: O(n), Space: O(n)
  - Not quite. The space is linear because the number of frames on the stack when it's at its deepest is proportional to the input size: specifically there will be `n` frames on the stack at the deepest layer. However, the time is not linear. What is the total number of stack frames over time if the array length is 2 versus 4?
- I don't know.
  - Don't worry. With time and practice, it'll start to sink in.

5. Mult choice

Calculate the time and space complexity for the following code. We've included both JS and Ruby for the same function.

<h3>JavaScript</h3>
<pre>
<code>
function balancingParentheses(string) {
  let missing = 0;
  let openings = 0;

  for (let i = 0; i < string.length; ++i) {
    if (string[i] === '(') {
      ++openings;
      continue;
    }

    if (openings > 0) {
      --openings;
    } else {
      ++missing;
    }
  }

  return missing + openings;
}
</code>
</pre>

<h3>Ruby</h3>
<pre>
<code>
def balancing_parentheses(string)
  missing = 0
  openings = 0

  string.chars.each do |char|
    if char == '('
      openings += 1
      next
    end

    if openings > 0 
      openings -= 1
    else
      missing += 1
    end
  end

  missing + openings
end
</code>
</pre>

- Time: O(n), Space: O(n)
  - Yes! The weakest links for time and space are the same thing: the input array. The algorithm must iterate over the entire array and it also has the potential to take up the most space. So both time and space are linear.
- Time: O(n), Space: O(1)
  - Not quite. The time complexity is linear, since the algorithm iterates over the entire array. It may seem like the space is constant because all of the additionally stored data is constant (integer variables). However, we have to consider the space taken by the input itself, which will scale linearly with the input.
- Time: O(n), Space: O(log n)
  - Not quite. The time complexity is linear, since the algorithm iterates over the entire array. For space complexity: what's the weakest link and how will the amount of space it requires change with the length of the input? Keep in mind that we must consider the amount of space taken up by the input also.
- I don't know.
  - Don't worry. With time and practice, it'll start to sink in.
