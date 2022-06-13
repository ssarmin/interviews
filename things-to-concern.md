# Sorting a 2D vector
for a `vector<vector<int>> v`

#### Custom sorting
You need add your custom fuction, like this one
```
    static bool my_option(string s1, string s2){
        return s1+s2 > s2+s1;
    }
```
And, call the sorting fuction like this
```sort(strs.begin(), strs.end(), my_option);```

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



# Priority queue

#### Default priority queue
Default STL priority queue is for max heap implementation

```
priority_queue<int> p;
```

#### Priority queue for min heap
```
priority_queue<int, vector<int>, greater<int> > p;
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
