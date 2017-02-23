### Standard Algorithms
1.  Print An Array
2.  Reverse A String 
3.  IsPalindrome 
4.  Find The Largest Number 
5.  Print A Pyramid 
6.  Print A Chess Board
6.  Phone Book 
7.  Binary
8.  Two Sum 
9.  Longest Substring With No Duplicates 
10.  Repeatify Using Prototypes 
11.  Stock Market Profit 
12.  DNA Strings 
13.  Randomize An Array
14.  Find The Products

### Recursion Specific 
1.  Reverse A String
2.  isPalindrome
3.  Factorial
4.  Sum Array Of Integers
5.  Flatten An Array 

***

### Print An Array
Write a function called `printArr` that will print the items of an array.

**Input:** ['sam','ed','harry']

**Output:** 
```javascript
    sam
    ed 
    harry
```
#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>

```javascript
function printArr(input){
    var string = "";
    for(var i = 0; i < input.length; i++){
        string += `${input[i]} \n`
    }
    return string;
}
```
</details>

### Reverse A String
Source: [leetcode](https://leetcode.com/problems/reverse-string/)
Write a function called `reverseString` that will take a string and return the string reversed.

**Input:** 'abcd'

**Output:** 'dcba’

**Hint:** Start by creating an empty string. Then using a loop in reverse order to concat a new string. 

#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
var reverseString = function(s) {
    var reverse = '';
    for(var i = (s.length-1); i >= 0; i--) {
        reverse += s[i];
    }
    return reverse;
}
```
</details>

#### Solution 2

**Hint:** Start by creating an array. Then add the right most elements to it (ie. the characters in reverse order) one by one. Then join and return it. 
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function reverseString(s) {
  const reverse = [];
  for (let i = (s.length - 1); i >= 0; i -= 1) {
    reverse.push(s[i]);
  }
  return reverse.join('');
}
```
</details>
### IsPalindrome
Write a function called `isPalindrome` that will return `true` if a given input (string(s) or number) is a palindrome and `false` if it's not. 

**Input:** 'race car' or 'Race car' or 12321

**Output:** true

#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function isPalindrome(s){
var s = s.toString().toLowerCase();
  let arr = s.split(' ').join('').split(''); 
  let reverseInput = [];
  arr.forEach((d) => reverseInput.unshift(d));
  return reverseInput.join("") == arr.join("");
}

```
</details>

#### Solution 2
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function isPalindrome(s) {
  var s = s.toString().toLowerCase();
  let arr = s.split(' ').join('').split(''); 
  for (let i = 0; i < arr.length / 2; i += 1) {
    if (arr[i] !== arr[arr.length - (i + 1)]) {
      return false;
    }
  }
  return true;
}
```
</details>
### Find The Largest Number
Write a function called `largestNumber` that will return the largest value from an array. 

**Input:** [1,2,5,10]

**Output:** 10
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function largestNumber(num){
    let largest = num[0]
    num.forEach((d) => {
        if(d > largest) { largest = d }
    })
    return largest
}
```
</details>
### Print A Pyramid
Write a function called `buildPyramid` that given a number, creates a pyramid that is that number of rows. 

**Input:** pyramid(4)

**Output:**
```javascript
            ^ 
           ^^^ 
          ^^^^^ 
         ^^^^^^^ 
```
#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function buildPyramid (rows) {
  const symbol = '^';
  let symbolCount = 1;
  let spaceCount = rows - 1;
  let pyramid = '';
  for (let i = 0; i < rows; i += 1) {
    let str = '';
    for (let j = 0; j < spaceCount; j += 1) {
      str += ' ';
    }
    for (let k = 0; k < symbolCount; k += 1) {
      str += symbol;
    }
    spaceCount -= 1;
    symbolCount += 2;
    pyramid += `${str}  \n`;
  }
  return pyramid
}


```
</details>
### Print A Chessboard
Source: [Eloquent Javascript](http://eloquentjavascript.net/code/#2.3)
Write a function called `chessBoard` that creates a string that represents an 8×8 grid, using newline characters to separate lines. At each position of the grid there is either a space or a “#” character. The characters should form a chess board.

**Input:** console.log(chessBoard())

**Output:** 
```javascript
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
```
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function chessBoard(){
  const size = 8;
  let board = '';
  for (let y = 0; y < size; y += 1) {
    for (let x = 0; x < size; x += 1) {
      if ((x + y) % 2 === 0) {
        board += ' ';
      } else {
        board += '#';
      }
    }
    board += '\n';
  }
  return board
}
```
</details>
### Odds And Evens
Source: [HackerRank](https://www.hackerrank.com/challenges/30-review-loop)
Write a function called `oddsEvens` that given a string, prints its even-indexed and odd-indexed characters as space-separated strings on a single line. 

**Input:** Hacker

**Output:** Hce akr

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function oddsEvens(input) {
  let left = '';
  let right = '';
  for (let i = 0; i < input.length; i += 1) {
    if (i % 2 === 0) {
      left += input[i];
    } else {
      right += input[i];
    }
  }
  return `${left} ${right}`;
} 
```
</details>
### Phone Book
Source: [HackerRank](https://www.hackerrank.com/challenges/30-dictionaries-and-maps)
Write a function called `phoneBook` that given two parameters, the first being an array of hashes containing n number of names and phone numbers and the second being an array of friends names will then will assemble a phone book that maps the 'friends' array of names to their respective phone numbers if they are found in the first array.  Each found entry will print the associated entry from your phone book on a new line in the form **name=phoneNumber**; if an entry is not found, print **Not found** instead.

**Input 1:** [{sam:99912222},{tom:11122222},{harry:12299933}]

**Input 2:** ['sam','ed','harry']

**Output:** 
```javascript
sam=99912222
NOT FOUND
harry:12299933
```
#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function phoneBook(input,mapped) {
  const contacts = [];
  const hash = {};
  const inputLen = input.length - 1;
  
  for (let i = 0; i <= inputLen; i += 1) {
    const contact = Object.keys(input[i]);
    hash[contact[0]] = input[i][contact];
  }
  for (let i = 0; i <= inputLen; i += 1) {
    let string = '';
    if (hash[mapped[i]]) {
      string += `${mapped[i]} = ${hash[mapped[i]]}`;
    } else {
      string += 'Not found';
    }
    contacts.push(string);
  }
  return contacts.join('\n')
} 
```
</details>
### Binary Count
Source: [HackerRank](https://www.hackerrank.com/challenges/30-binary-numbers)
Write a function called `binaryCount` that given a base integer, converts it to binary and then finds and prints maximum number of consecutive '1's in binary. 

Example:
**Input:** 60 which is 111100 in binary

**Output:** 4

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function binaryCount(num){
  const b = Number(num).toString(2);
  let longest = 0;
  let count = 0;
  for (let i = 0; i < b.length; i += 1) {
    if (Number(b.charAt(i))) {
      count += 1;
    } else {
      if( count > longest) { longest = count; }
      count = 0;
    }
  }
  if( count > longest ) { longest = count; }
  return longest;
}
```
</details>
### Two Sum
Source: [Leetcode](https://leetcode.com/problems/two-sum/)
Write a function called `twoSum` that given an array of integers and a target number, returns two array integers that add up to the target.

**Input:** [3, 2, 5, 7, 11, 15], 9

**Output:** Return [2, 7] 

**Hints**
* Try to think of a data structure that works best for returning the first matched value it finds. 
* Think about how using a compliment could be used in this scenario: if your target is 9 and you're looking at 2, what is its complement?

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function twoSum(arr, target) {
  const hash = {};
  for (let i = 0; i < arr.length; i += 1) {
    const val = arr[i];
    const complement = target - val;
    if (hash[complement] !== undefined) {
      return [val, complement];
    }
    hash[val] = i;
  }
  return null;
}
```
</details>
### Longest Substring With No Duplicates
Source: [Leetcode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
Write a function called `lengthOfLongestSubstring` that given a string, finds the length of the longest substring without repeating characters.

**Input:** 'abca'

**Output:** 3 ('abc' or 'bca')

**Input:** 'abcbadb'

**Output:** 4 ('cbad')

**Hints**

* Try using a "sliding window".  This uses two pointers, one for the head and the other for the tail. They are then incremented\decremented until they reach a mid way point in the string. 
* How can you decide when to increment the head and the tail? (Answer: always increment tail by one and move the head whenever you encounter a dup.

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function lengthOfLongestSubstring(s) {
  let head = 0;
  let longest = 0;
  const hash = {};
  for (let tail = 0; tail < s.length; tail += 1) {
    const ch = s[tail];
    if (hash[ch] !== undefined && hash[ch] >= head) {
      longest = Math.max(longest, tail - head);
      head = hash[ch] + 1;
    }
    hash[ch] = tail;
  }
  longest = Math.max(longest, tail - head);
  return longest;
}
```
</details>
### Repeatify (using prototypes)
**Part 1:** Write a function called `repeatify` that takes a string and a number.  The number specifies how many times the string should be repeated.

**Input:** repeatify("hello", 3);

**Output:** "hellohellohello"

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function repeatify(str, n) {
  let result = '';
  for (let i = 0; i < n; i += 1) {
    result += str;
  }
  return result;
}
```
</details>
**Part 2:** Let’s update the function so it’s a string method.  Change your code from part 1 so we can call repeatify on a string and just pass it a number.

**Input:** "hello".repeatify(3);

**Output:** "hellohellohello"

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
String.prototype.repeatify = function(n) {
  let result = '';
  for (let i = 0; i < n; i += 1) {
    result += this;
  }
  return result;
};
```
</details>
### Stock Market Profit
Source: [InterviewCake](https://www.interviewcake.com/question/javascript/stock-price)
Write an function called `getMaxProfit` that takes in an array of stock prices and returns the best profit you could have made from 1 purchase and 1 sale.  The prices in the array are in the sequence in which they were purchased and can only be sold after it was first purchased.

**Input:** getMaxProfit([10, 7, 5, 8, 11, 9])

**Output:** 6 ..this is the result of 11 - 5

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
stock_prices_yesterday = [10, 7, 5, 8, 11, 9]

function getMaxProfit(stockPricesYesterday) {
    if (stockPricesYesterday.length < 2) {
      throw new Error('Getting a profit requires at least 2 prices');
    }

    let minPrice = stockPricesYesterday[0];
    let maxProfit = stockPricesYesterday[1] - stockPricesYesterday[0];
    for (let i = 1; i < stockPricesYesterday.length; i += 1) {
      const currentPrice = stockPricesYesterday[i];
      const potentialProfit = currentPrice - minPrice;
      maxProfit = Math.max(maxProfit, potentialProfit);
      minPrice = Math.min(minPrice, currentPrice);
    }
    return maxProfit;
}
```
</details>
### DNA Strings
Source: [CodeWars](https://www.codewars.com/kata/554e4a2f232cdd87d9000038)
In DNA strings, symbols "A" and "T" are complements of each other, as are "C" and "G". Write a function called `dnaTransform` that takes in a DNA string returns a string that represents it's compliment. 

**Input:** dnaTransform("ATTGC")

**Output:** "TAACG"

#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
var dna = "ATTGC";
function dnaTransform(dna){
  const dnaObj = { A: 'T', T: 'A', G: 'C', C: 'G' };
  return dna.split('').map((d) =>  dnaObj[d] );
}
```
</details>
#### Solution 2
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
const dna = "ATTGC";
function dnaTransform(dna){
  const outArr = [];
  const newDna = dna.split('');
  newDna.forEach((d, i) => {
    switch (d) {
      case 'G': outArr[i] = 'C'; break;
      case 'T': outArr[i] = 'A'; break;
      case 'A': outArr[i] = 'T'; break;
      case 'C': outArr[i] = 'G'; break;
    }
  });
  const str = outArr.join('');
  return str;
}
```
</details>
### Randomize An Array
Source: [Fisher-Yates Shuffle](https://bost.ocks.org/mike/shuffle/)
Write a function called `shuffle` that given an array, randomizes the position of the elements and returns the new array. 

**Input:** shuffle(['a','b','c','d'])

**Possible Output:** ['b','d','a','c']

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function shuffle(array) {
  let len = array.length;
  let last;
  let random;
  while (len) {
    random = Math.floor(Math.random() * (len -= 1));
    last = array[len];
    array[len] = array[random];
    array[random] = last;
  }
  return array;
}
```
</details>
### Find The Products
Source: [InterviewCake](https://www.interviewcake.com/question/javascript/product-of-other-numbers)
Write a function called `getProducts` that takes in an array of n numbers and for each index finds the product of every integer **except** the integer at that index.

**Input:** getProducts([1,2,3,4])

**Output:** [ 24, 12, 8, 6 ]

#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function getProducts(input) {
  const products = [];
  let productSoFar = 1;
  for (var i = 0; i < input.length; i += 1) {
    products[i] = productSoFar;
    productSoFar *= input[i];
  }
  productSoFar = 1;
  for (var j = input.length - 1; j >= 0; j -= 1) {
    products[j] *= productSoFar;
    productSoFar *= input[j];
  }
  return products;
}
```
</details>

#### Solution 2
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function getProducts(arr) {
  const newArr = [];
  for (let i = 0; i < arr.length; i += 1) {
    let testArr = arr.map(d => d);
    testArr.splice(i, 1);
    newArr.push(testArr.reduce((a, b) => a * b));
  }
  return newArr;
}
```
</details>
##Recursion Specific

### Reverse A String 
Source: [Ten Ways To Reverse A String](http://eddmann.com/posts/ten-ways-to-reverse-a-string-in-javascript/)
#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function reverse(s) {
  return (s === '') ? '' : reverse(s.substr(1)) + s.charAt(0);
}
```
</details>
#### Solution 2
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function reverse(s) {
  function rev(s, len, o) {
    return (len === 0) ? o : rev(s, len -= 1, (o += s[len]));
  }
  return rev(s, s.length, '');
}
```
</details>
### isPalindrome
Source: [CodeChewing](http://www.codechewing.com/library/recursive-javascript-function/)
<details>
  <summary><strong>Click to reveal...</strong></summary>
  ```javascript
function isPalindrome(string) {
  if (string.length <= 1) { return true; }
  if (string.charAt(0) !== string.charAt(string.length - 1)) { return false; }
  return isPalindrome(string.substr(1, string.length - 2));
}
```
</details>


### Factorial
Source: [HackerRank](https://www.hackerrank.com/challenges/30-recursion/submissions/code/37642498)
Given a number, print it's factoral.

**Input:** 5 

**Output:** 120 (5*4*3*2*1)

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function factoralize(input) {
  function factorial(num) {
    return num === 1 ? 1 : num * factorial(num - 1);
  }
  return factorial(parseInt(input, 10));
}
```
</details>

### Sum Array Of Integers
Source: [W3Resource](http://www.w3resource.com/javascript-exercises/javascript-recursion-functions-exercises.php?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+w3resource+%28w3resource%29)
Write a function to compute the sum of an array of integers.

**Input:** [1,2,3]

**Output:** 6

#### Solution
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function arrSum(arr) {
  if (arr.length === 1) {
    return arr[0];
  }
  else {
    return arr.pop() + arrSum(arr);
  }
};
``` 
</details>

### Flatten An Array
Source: [CodeTuts](https://codetuts.tech/flatten-deep-nested-array-object/)
Write a function that takes an array and flattens it.  You can assume the array only contains arrays and primitives (Numbers, Strings, Booleans, etc.).

**Input:** [1,[2,3],[[4], 5]]

**Output:** [1, 2, 3, 4, 5]

#### Solution 1
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function fh(arr, result) {
    arr.forEach(function(elm) {
        if (Array.isArray(elm)) {
            fh(elm, result);
        } else {
            result.push(elm);
        }
    });
    return result;
}

function flatten(arr) {
    return fh(arr, []);
}
```
</details>
#### Solution 2
<details>
  <summary><strong>Click to reveal...</strong></summary>
```javascript
function flatten(arr) {  
  return arr.reduce((a, b) => {
    return a.concat( Array.isArray(b) ? flatten(b) : b );
  }, []);
}
```
</details>

