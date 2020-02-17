```
// ----------------------------------- Syntax -----------------------------------

// Single-line comments start with two slashes.
/* Multiline comments start with slash-star,
   and end with star-slash */

// White space does not matter

// ----------------------------------- Literals -----------------------------------

// Strings are created with ', " or `.
'abc'
"Hello, world"

// Numbers includiung complex values
15                // a number
0b111             // binary => 7
0o111             // octal => 73
0x111             // hexadecimal => 273
(1 2) :complex    // complex numbers

// There's also a boolean type.
true
false
null      // used to indicate a deliberate non-value (neither true nor false)

// Words
thing:        // this is a key, it is not execuated unless evaluated
thing         // a word that is executed immediatly unless enclused in an lazy array
:thing        // a word that is executed immediatly even if it is inclused in an lazy array
#thing        // a unique symbol

// ----------------------------------- Arrays -----------------------------------

// Active arrays
(1 2 3) // => [ 1 2 3 ]
(1 2 +) // => [ 3 ]
('Hello' 'World' +)  // => [ "Hello World" ]

// Lazy Arrays
[1 2 3] // => [ 1 2 3 ]
[1 2 +] // => [ 1 2 + ]
['Hello' 'World' +]  // => [ "Hello" "World" + ]

// Construction and concatination
1 unit          // [ 1 ]
[ 2 ] 3 <<      // [ 2 3 ]
5 [ 8 ] >>      // [ 5 8 ]
[ 13 ] [ 21 ] + // [ 13 21 ]

// `ln` is returns the length.
[ 5 8 13 ] ln // => 3
'Hello' ln    // => 5

// Arrays are zero-based, negitive for access from the back
[ 'first' 'second' ] 1 @  // => 'first'
'This is a string' 0 @    // => 'T'
[ 'first' 'second' ] -2 @  // => 'first'
'This is a string' -1 @   // => 'g'

// Some access words
[ 'first' 'second' ] first   // => 'first'
'This is a string' last    // => 'g'

// Arrays can be evaluated
2 [ 3 + ] eval  // => 5

// Map and filter
[ 1 2 3 ] [ 2 * ] map   // => [ 2 4 6 ]
[ 1 2 3 ] [ < 2 ] map   // => [ 1 ]

// ----------------------------------- Maps -----------------------------------

// Maps
{ x: 1 y: 2 }        // => { x: 1, y: 2 }
{ x: 1 y: 2 } 'x' @  // => 1
{ x: 1 } { y: 2 } +  // => { x: 1, y: 2 }

// ----------------------------------- Words -----------------------------------

// `println` pops the top result from the stack and prints it.
9 println    // 9

// Math is straightforward
6 7 *       // 42
1360 23 -   // 1337
12 12 /     // 1
13 2 %      // 1
99 ~        // -99
2 3 ^       // 8
10 ln       // 2.302585092994046

(1 2) :complex (6 -4) :complex +  // 7-2i

// And boolean operations
true false +  // OR
true false *  // AND
true ~        // NOT

// Comparisons
'a' 'b' <=>   // 1
2 1 <=>       // -1
2 1 <=>       // -1
'x' 'x' <=>   // 0

// Equality is = and inequality is !=
1 1 =   // => true
2 1 =   // => false
#x #x = // => false
4 5 !=  // => true

// and are compared with < and >
"a" "b" <  // => true
"a" "b" >= // => false

// A number of words are provided to manipulate the stack, collectively known as shuffle words.
3 dup -           // duplicate the top item (1st now equals 2nd): 3 - 3
2 5 swap /        // swap the top with the second element:        5 / 2
4 0 drop 2 /      // remove the top item (don't print to screen):  4 / 2
1 2 clear         // wipe out the entire stack
1 2 3 4 over      // duplicate the second item to the top: 1 2 3 4 3
1 2 3 4 2 pick    // duplicate the third item to the top: 1 2 3 4 2 3

// ----------------------------------- Word Defintions -----------------------------------

// Defining new words
square: [ dup * ] def   // No output
5 square                // 25

x: 1 def                // creates a function that always returns 1

// We can view what a word does too.
'square' show
[ dup * ]

// ----------------------------------- Control Flow -----------------------------------

true                  // test expression
  'this is true'      // then expression
  'this is false'     // else expression
  choose
// => 'this is true'

5 [ "Five is true" ] when                       // => Five is true
0 [ "Zero is true" ] when                       // => Zero is true
false [ "F is true" ] when                      // => No output
false [ "F is false" ] unless                   // => F is false
2 [ "Two is true" ] [ "Two is false" ] branch   // => Two is true

// ----------------------------------- Modules and namespaces -----------------------------------

```