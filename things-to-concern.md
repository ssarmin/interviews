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
#### Increasing order sort by Col
```
    static bool sortcol(const vector<int>& v1, const vector<int>& v2){
        return v1[1] < v2[1];
    }
    sort(v.begin(), v.end(), sortcol);
```
#### Decreasing order sort by Col




# Iterating an array

#### Increasing order
```
  for(unsinged int i=0; i<arr.size(); ++i){
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

