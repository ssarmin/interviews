# This part is mainly for C++ #
## Edge cases ##
1. Check whether the given list/array is empty



## Complexity improvement ##
1. For getting access to the last element of a vector, use `v.back()` instead of having an `index` variable to keep track, variable might get out of sync, might create error.
2. for looping through a vector, use `for (const auto& v : arr)` instead of `for(auto i=0; i<arr.size(); i++)`. Passed by reference (`const auto&`): This prevents copying the inner `vector<int>` during each iteration of the loop, which saves a bit of overhead.
3. if possible allocate space for the vector, `v.reserve()`
4. 
   
