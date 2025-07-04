# Sorting a 2D vector
for a `vector<vector<int>> v`

#### Increasing order for 1st row
```
sort(v[0].begin(), v[0].end());
```
#### Decreasing order for 1st row
```
sort(v[0].rbegin(), v[0].rend());
```
#### Increasing order sort by 2nd Col 
```
    static bool sortcol(const vector<int>& v1, const vector<int>& v2){
        return v1[1] < v2[1];
    }
    sort(v.begin(), v.end(), sortcol);
```
#### Decreasing order sort by Col

#### Vector with object sort
```
/**
 * Definition of Interval:
 * class Interval {
 * public:
 *     int start, end;
 *     Interval(int start, int end) {
 *         this->start = start;
 *         this->end = end;
 *     }
 * }
 */

// Comparator function to sort intervals by their start value
static bool compareIntervals(const Interval& i1, const Interval& i2) {
    return i1.start < i2.start;
}
vector<Interval> intervals;
sort(intervals.begin(), intervals.end(), compareIntervals);

```
# String sorting

#### Custom sorting

If we have strings, ```vector<string> str = {"1", "99", "888", "5", "9"};``` We want to get the string sorted accodring to the numeric value of the string, like this ```"1", "5", "9", "99", "888"```;

If we use normal sorting for this ```sort(str.begin(), str.end());```. we will get this output ```"1", "5", "888", "9", "99" ```

To get our targeted outcome, we need to have a custom comparision function in the sorting: ```sort(str.begin(), str.end(), my_func);```

```
    static bool my_func(string s1, string s2){
        if(s1.size() == s2.size())
            return s1 < s2;
        return s1.size() < s2.size();
    }
```

Another custom function:

You need add your custom fuction, like this one
```
    static bool my_option(string s1, string s2){
        return s1+s2 > s2+s1;
    }
```
And, call the sorting fuction like this
```sort(strs.begin(), strs.end(), my_option);```

# Reversing an array
#### Reversing the whole array
```
reverse(arr.begin(), arr.end());
```

#### Reversing first `n` elements
```
reverse(arr.begin(), arr.begin()+n);
```

#### Reversing the rest of the elements (whole array - first `n` elements)
```
reverse(arr.begin()+n, arr.end());
```

# Iterating an array

#### Increasing order
```
  for(unsigned int i=0; i<arr.size(); ++i){
  ...
  }
```

as the index of an array would be always positive, that's why selecting unsigned int


#### Decreasing order
```
   for(unsigned int i=arr.size()-1; i>=0; --i){
   ...
   }
```

This might not work always as it's unsigned int from `i=0`, the next value of `i` could be `MAX_UINT`.

To solve this issue,

```
   for(unsigned int i=arr.size()-1; i>=0; --i){
   ...
   if(i==0)
    break;
   }
```

or

```
   for(int i=arr.size()-1; i>=0; --i){
   ...
   }
```

## Adding value and vector to 2D vector without creating new 1D vector

Here's a 2D `vector<vector<int>> res`


`res.emplace_back();` directly construct a vector inside `res`


`res.back()` to access it


`res.back().push_back(val);`

# Priority Queue

#### Default priority queue
Default STL priority queue is for max heap implementation

```
priority_queue<int> p;
```
The value having a greater element is the topmost element.
 
#### Creating a priority queue from a vector
If the given vector is `v`


```priority_queue<int> p(v.begin(), v.end());```

#### Priority queue for min heap
```
priority_queue<int, vector<int>, greater<int> > p;
```
For this priority queue, the value having a smaller element is the topmost element.


#### Priority queue of sets

```priority_queue<set<data_type>> pq;```
This stores set as an element in the max-heap priority queue. 
The set having a greater first element is the topmost element. If the first element is equal then the second value of sets is compared and so on.

To set priority_queue to work as a min-heap:
```priority_queue<set<data_type>, vector<set<data_type>>, greater<set<data_type>>> pq;```



# Map access
#### To access at the begin of a map
```
map<int, int> m;
auto it = m.begin();
```
To access at an Index `r` of a map
```
advance(it, r);
```

To check whether a key is present or not:
```
map_name.count(key k)
```
```count()``` returns 1 if the element with key K is present in the map container, otherwise 0.


# BFS - DFS
For BFS, make sure marking position visited before entering the queue, that would ensure that we are not enqueuing same position multiple times.
We will traverse one position only once!

For DFS, make sure marking position visited before entering the stack, that would ensure that we are not pushing same position multiple times.
We will traverse one position only once!

# Create new String with repeated character

If I want to create a ```string str = "aaaaa"``` where the character ```a``` is a variable, ```ch```
we can create it this way

```
   char ch = 'a';
   int num = 5;
   string str(num, ch);
```

# Remove the last character from a string
```
if(!str.empty()){
    str.pop_back();
}
```
# String concatenation
If we have a ```string word``` which we want to append to ```string result```.

Non-efficient approach
```
result = result + word + " ";
```
In this approach, ```result``` grows with each concatenation, so repeated string concatenation like this costs ```O(1 + 2 + 3 + ... + n) = O(n²)``` in the worst case (due to repeated reallocation and copying).
Time complexity: ```O(n²)```

Efficient approach
```
ostringstream result;         // Efficient string builder
result << word << " ";              // Append to result with space

string res = result.str();              // Convert stream to string
```

In this approach, ```ostringstream``` accumulates characters efficiently without frequent memory reallocations.

All operations (reverse, splitting, appending) are linear in total characters.

# String split by space

We have a ```string str``` which contains word and spaces. We want to get the words from the string.

```
    istringstream ss(str);
    string word;
    
    while (ss >> word){
        // use the word
    }
```

If we have a ```string str = "adsf+qwer+poui+fdgh";``. We want to get the words from the string which are sperated by ```+```.
```
        istringstream ss (s);
        string word;
        char delim = '+';
        
        while (getline (ss, word, delim)) {
            // use the word
        }
```

# unordered_set
an unordered associative container that stores unique elements. Unlike set, it stores its elements using hashing. This provides average constant-time ```O(1) search, insert, and delete operations``` but the elements are not sorted in any particular order.

# log
for Java, log10(n) / log10(3) could be 5.0000001 or 4.9999999. This effect can be observed by using the function log() instead of log10().
for C++, use log2()

# Hashing
If you are using key/hash based containers, your key size should be small to avoid TLE.

# Trie
The complexity of creating a trie is ```O(W*L)```, where ```W``` is the number of words, and ```L``` is an average length of the word. You need to perform ```L``` lookups on the average for each of the ```W``` words in the set.

# Stack
We can modify any value in the top element of stack without popping and repushing. Like this
```
stack<pair<int, char>> s;
s.push({11, 'f'});
cout << s.top().first << endl; // this will output 11
s.top().first = 15;
cout << s.top().first << endl; // Now, this will output 15
```
