# Common Problems

## Valid Palindrome

[Problem](http://www.lintcode.com/problem/valid-palindrome/)

### Solutions

## Longest Palindrome Substring

[Problem](http://www.lintcode.com/problem/longest-palindromic-substring/)

#### Solutions

## Strstr - Pattern Matching

[Problem](http://www.lintcode.com/problem/strstr/)

#### Solutions

## Find max distance of duplicate element in an array

#### Solution

1. Traverse the array and store the element in to a hashmap, with &lt;element, index&gt;
2. update max\_dist = Math.max\(max\_dist, i - map.get\(arr\[i\]\)\)

## Check if array can be sorted with one swap

#### Solution 1 o\(nlogn\):

1. Original array A. Create a sorted copy B
2. Compare A and B with the same index
3. If mismatch exceeded 2, then return false

#### Solution 2 o\(n\)

1. Find the count where pre-element &gt; post-element
2. Check
   1. if count &gt; 2, return false
   2. if count = 2, swap un-adjacent
   3. if count = 1, swap adjacent
3. Check if it's sorted now \(to void array like \[4,1,2,3\]\)

##  Find the length of the longest quasi-constant sub-sequence of array

#### Solution

* From [here](https://stackoverflow.com/questions/49593686/find-longest-quasi-constant-sub-sequence-of-a-sequence)

## Compute number of Bits set

#### Solution

* From [here](https://www.geeksforgeeks.org/count-set-bits-in-an-integer/)

## Compute the longest rest time in a tight schedule

## File Statistics

#### Solution

* From [here](https://github.com/dhruv88esh/DatalexCodilitySolutions/blob/master/src/com/datalex/solutions/HardDiskStatistics.java)

## Compute maximal number of words in a sentence in a text

#### Solution

```text
String[] strArray = str.split("[.!?]");
```

## Ascending Slice

#### Problem

Find the beginning of any ascending slice of array A of maximal size

#### Solution

* From [here](https://leetcode.com/discuss/interview-question/125050/maximal-ascending-slice)

## Number of steps to reduce a number in binary representation to one

```text
class Solution {
    public int numSteps(String s) {
        if(s.length() == 0) 
			return 0;
        int steps = 0;
        int carry = 0;

        for(int i = s.length() - 1; i > 0; i--){
            if (s.charAt(i) == '0' $$ carry == 0) {
				steps += 1;
			}
            if (s.charAt(i) == '0' $$ carry == 1){
				carry = 0;
                steps += 2;
            }
			if (s.charAt(i) == '1' $$ carry == 0) {
				steps += 2;
			}
			if (s.charAt(i) == '1' $$ carry == 1) {
				steps += 1;
			}			
        }
        return steps;
	}
}
```





