## GFG Problem Of The Day

### 🎉 Announcement
I have created a Git Book that contains all previous editorials for my GFG-POTD solutions. You can visit **[here](https://gl01.gitbook.io/gfg-editorials/)** to access it and refer to my previous solutions. In the future, I intend to establish a contribution flow, where others can contribute their solutions to this Git Book. I would appreciate hearing your thoughts and views on this in the [discussion section](https://github.com/getlost01/gfg-potd/discussions).

----
### Today - 06 August 2023
### Que - String Permutations

The problem can be found at the following link: [Question Link](https://practice.geeksforgeeks.org/problems/permutations-of-a-given-string-1587115620/1)

### My Approach

To find all the permutations of a given string `s`, we can use a backtracking approach. 
- The idea is to swap characters at different positions and recursively generate all possible permutations. 
- We start with the first character `s[0]` and swap it with every other character in the string. Then, we recursively find all permutations of the remaining characters. 
- After generating all permutations, we sort the result vector to ensure the output is in lexicographically sorted order.

### Time and Auxiliary Space Complexity

- **Time Complexity**: `O(N!)`, where `N` is the length of the input string `s`. This is because there are `N!` permutations possible for a string of length `N`.
- **Auxiliary Space Complexity**: `O(N!)` because the `out` array will store all the permutations,

### Code (C++)

```cpp
class Solution{
public:
    vector<string> out;

    void check(string &s, int i, int &n){
        if(i == n){
            out.push_back(s);
            return; 
        }
        
        for(int j = i; j < n; ++j){
            swap(s[i], s[j]);
            check(s, i+1, n); 
            swap(s[i], s[j]); 
        }
    }
  
    vector<string> permutation(string s){
        int n = s.size(); 
        check(s, 0, n); 
        sort(out.begin(), out.end());
        return out; 
    }
};
```
### Contribution and Support

I always encourage contributors to participate in the discussion forum for this repository.

If you have a better solution or any queries / discussions related to the `Problem of the Day` solution, please visit our [discussion section](https://github.com/getlost01/gfg-potd/discussions). We welcome your input and aim to foster a collaborative learning environment.

If you find this solution helpful, consider supporting us by giving a `⭐ star` to the [getlost01/gfg-potd](https://github.com/getlost01/gfg-potd) repository.


![Total number of repository visitors](https://komarev.com/ghpvc/?username=gl01potdgfg&color=blue&&label=Visitors)
