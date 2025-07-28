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

#### Priority queue custom comparator
```priority_queue<pair<int, int>, vector<pair<int, int>>, Compare> pq;```

This stores pair as an element in the min-heap priority queue. We want to get the pair that provides the smallest summation. 


The custom comparator:
```
class Compare {
    public:
        bool operator()(pair<int, int> p1, pair<int, int> p2){
            // When true is returned, it means the order is NOT correct and swapping of elements takes place.
            if (p1.first + p1.second > p2.first + p2.second) {
                return true;
            }
            
            // When false is returned, it means the order is correct and NO swapping of elements takes place.
            return false;
        }
};
```
# Map access
### To access at the begin of a map
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

### map lower_bound and upper_bound

| Function       | What it does                                                |
| -------------- |:-----------------------------------------------------------:|
| lower_bound(k) | Finds the first key that is ≥ (greater than or equal to) k  |
| upper_bound(k) | Finds the first key that is > (strictly greater than) k     |

Example:
If your map has keys: [10, 20, 30]

lower_bound(20) → points to 20

upper_bound(20) → points to 30

lower_bound(25) → points to 30

upper_bound(25) → points to 30

lower_bound(35) → points to end() (nothing ≥ 35)

upper_bound(35) → points to end() (nothing > 35)

<!---
### map lower_bound

find the first element in the map whose key is either equal to or greater than the given key. If the key passed in the parameter exceeds the maximum key in the container, then the iterator returned points to the number of elements in the map container as key and nothing for the element.

```
    map<int, char> m = {{10, 'A'}, {20, 'B'},
                        {30, 'C'}};
    int k = 20;

  	// Find the lower bound
    auto it = m.lower_bound(k);
  	cout << it->first << " " << it->second << endl;
  
  	it = m.lower_bound(30);
  	cout << it->first << " " << it->second << endl;
  
  	it = m.lower_bound(35);
  	cout << it->first << " " << it->second << endl;
```

output of this code would be

```
20 B
30 C
3 
```

### map upper_bound

find immediate next element just greater than k. If the key passed in the parameter exceeds the maximum key in the container, then the iterator returned points to the number of elements in the map container as key and element=0.

```
    map<int, int> mp;

    // insert elements in random order
    mp.insert({ 12, 30 });
    mp.insert({ 11, 10 });
    mp.insert({ 15, 50 });
    mp.insert({ 14, 40 });

    // when 11 is present
    auto it = mp.upper_bound(11);
    cout << "The upper bound of key 11 is ";
    cout << (*it).first << " " << (*it).second << endl;

    // when 13 is not present
    it = mp.upper_bound(13);
    cout << "The upper bound of key 13 is ";
    cout << (*it).first << " " << (*it).second << endl;

    // when 17 is exceeds the maximum key, so size
        // of mp is returned as key and value as 0.
    it = mp.upper_bound(17);
    cout << "The upper bound of key 17 is ";
    cout << (*it).first << " " << (*it).second;
}
```

output of this code would be
```
The upper bound of key 11 is 12 30
The upper bound of key 13 is 14 40
The upper bound of key 17 is 4 0
```
--->
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
# Append a character at the end a string
```
char ch = 'a';
str.push_back(ch);
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

# tuple
```
tuple<int, char, string, int,...> t{0, 's', "stsfsf", 4,....}
```
Get the values from the tuple

```
auto [index, ch, str, val, ....] = t;
```

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
