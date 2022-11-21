# Comparators

<details>
<summary>simple comparator</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void add(int& e) {
    ++e;
}

void modify(vector<int>& _vec, const function<void(int&)>& _add) {
    for (int& e : _vec)
        _add(e);
}

int main() {
    vector<int> vec {1, 2, 3, 4, 5};
    modify(vec, add);
    for (int& e: vec)
        cout << e << ' ';
}
```

<details>

# Iterators

<details>
<summary>iterators</summary>

```
#

- random access > bidirectional > forward > input, output
- container<type>::iterator it

            string    random access
             array    random access
            vector    random access
             deque    random access

      forward_list    forward
              list    bidirectional

               set    bidirectional
          multiset    bidirectional
     unordered_set    forward
unordered_multiset    forward

               map    bidirectional
          multimap    bidirectional
      uordered_map    forward
unordered_multimap    forward

             stack    x
             queue    x
    priority_queue    x

# iterator operations

// bidirectional, moves 'it' by cnt
// cnt can be -ve
- advance(it, cnt) 

// random access, [it_f, it_l)
// returns -ve value if it_f > it_l
- distance(it_f, it_l) 

// bidirectional, 'it' is unchanged
// returns new iterator pos
- next(it, cnt) 
- prev(it, cnt)
```

</details>

<details>
<summary>input iterator</summary>

```
- used for accessing values
- can be compared
  A == B
  A != B
- dereferencing using * and -> // only as r-value
  x = *A
  x = A->first, x = A->second
- can only be incremented
  ++A, A++
  A + 1, A - 5 // not allowed
- can be swapped
  swap(A, B)
```

</details>

<details>
<summary>output iterator</summary>

```
- used for assigning values
- can be compared
  A == B
  A != B
- dereferencing using * and -> // only as l-value to store the given value
  *A = x
  A->first = x, A->second = x
- can only be incremented
  ++A, A++
  A + 1, A - 5 // not allowed
- can be swapped
  swap(A, B)
```

</details>

<details>
<summary>forward iterator</summary>

```
- accessing and assigning
- can be compared
  A == B
  A != B
- dereferencing using * and -> // r-value and l-value
  x = *A
  x = A->first, A->second = x
- can only be incremented
  ++A, A++
  A + 1, A - 5 // not allowed
```

</details>

<details>
<summary>bidirectional iterator</summary>

```
- forward iterators which can move back
  --A, A--, ++A
  A + 1, A - 5 // not allowed
```

</details>

<details>
<summary>random access iterator</summary>

```
- bidirectional iterators which
- can be compared
  A == B
  A != B
  A >= B
  ...
- A + 1, A - 5 // allowed
- offset dereference operator '[]'
  A[7] // valid
```

</details>

# Strings

<details>
<summary>basic string</summary>

```
#

- string str {"..."}
  string str iList
  string str (cnt, ch)
  string str (other_str, idx_other_str, cnt) // cnt from idx
  string str (it_f, it_l) // [it_f, it_l)

- str.assign("...")
  str.assign(iList)
  str.assign(cnt, ch)
  str.assign(other_str, idx_other_str, cnt)
  str.assign(it_f, it_l)

- str = "..."
  str = iList
  str = other_str

# random access iterator

- str.begin()
  str.cbegin()
  str.rbegin()
  str.crbegin()

- str.end()
  str.cend()
  str.rend()
  str.crend()

# element access

- str[idx] // no bounds checking, for performance
- str.at(idx) // bounds checking
- str.front()
- str.back()

# capacity

- str.empty()
- str.size()

# operations

- str.clear()

- str.erase(idx, cnt)
  str.erase(it_f, it_l)

- str.insert(idx, "...")
  str.insert(idx, iList)
  str.insert(idx, cnt, ch)
  str.insert(idx, other_str, idx_other_str, cnt) // idx can be str.size(), behaves as str.append()

- str.push_back(ch) // only a character
- str.pop_back()

- str.append("...")
  str.append(iList)
  str.append(cnt, ch)
  str.append(other_str, idx_other_str, cnt)

// calls str.append()
- str += "..."
  str += iList
  str += other_str
  str = other_str + str // inefficient

// lexicographically compared
// smalls > caps as in ASCII table
   return val < 0 for str < other_str
          val = 0 for str = other_str
          val > 0 for str > other_str
- str.compare(idx, cnt, "...")
  str.compare(idx, cnt, iList)
  str.compare(idx, cnt, cnt_ch, ch)
  str.compare(idx, cnt, other_str, idx_other_str, cnt_other_str)

- str.replace(idx, cnt, "...")
  str.replace(idx, cnt, iList)
  str.replace(idx, cnt, cnt_ch, ch)
  str.replace(idx, cnt, other_str, idx_other_str, cnt_other_str)

- str.substr(idx, cnt) // returns sub string

# search

// returns position of the first character of the found substring
// or string::npos if no such substring is found
- str.find("...", idx) // search from idx of str
  str.find(iList, idx)
  str.find(other_str, idx)

// search from end
// still compared from ltr
- str.rfind("...", idx)
  str.rfind(iList, idx)
  str.rfind(other_str, idx)

# constants

- string::npos
  // although npos = -1, npos represents the largest positive value as it is unsigned
  // str.find(other_str) returns string::npos if other_str is not found

# numeric conversions

- stoi(str, nullptr, base) 
  // returns a base10 integer
  // str read in base 'base'
  // first non-space characater must be an integer charcater
  stoi(" 59z8") // 59
  stoi(" 5 9z8", nullptr, 10) // 5
  stoi("  m59z8") // invalid
  stoi("   21g ", nullptr, 8) // 17
  stoi(" -1aj", nullptr, 16) // -26

- stol(str, pos, base)
- stoll(str, pos, base)
- stoul(str, pos, base)
- stoull(str, pos, base)
- stof(str, pos, base)
- stod(str, pos, base)
- stold(str, pos, base)

- to_string(int../float..)

#

// return 'false' if not
- isalpha(ch)
- isdigit(ch)
- isalnum(ch)
- isspace(ch)
- ispunct(ch) // !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
- islower(ch)
- isupper(ch)

#

- tolower(ch)
- toupper(ch)
```

</details>

# Containers

<details>
<summary>C style array</summary>

```
#

- T arr[] iList
  T arr[cnt] iList
  T arr[][cnt][cnt] iList

# element access

- arr[n] // *(arr + n)
  n[arr] // *(n + arr)

  arr[n][o] // *(*(arr + n) + o)
  o[n[arr]]

# array vs pointer

- sizeof(arr) returns memory occupied by all elements in the array.
- sizeof(ptr) returns memory occupied by the pointer.

- arr returns address of the first element.
  arr = &arr[0]
- ptr returns the assigned address.
```

</details>

#### sequence

<details>
<summary>array</summary>

```
#

- array<T, cnt> arr iList
  array<array<T, cnt>, cnt> arr iList

- arr = other_arr

# random access iteratr

- arr.begin()
  arr.cbegin()
  arr.rbegin()
  arr.crbegin()

- arr.end()
  arr.cend()
  arr.rend()
  arr.crend()

# element access

- arr[idx]
- arr.at(idx) // bounds checking
  arr.at.at...()
- arr.front()
- arr.back()

# capacity

- arr.empty()
- arr.size()
```

</details>

<details>
<summary>vector</summary>

```
- vector<bool> is optimized for space efficiency

#

- vector<T> vec iList
  vector<T> vec (cnt, val)
  vector<T> vec (other_vec)
  vector<T> vec (it_f, it_l)

- vec.assign(iList)
  vec.assign(cnt, val)
  vec.assign(other_vec)
  vec.assign(it_f, it_l)

- vec = iList
  vec = other_vec

# random access iterator

- vec.begin()
  vec.cbegin()
  vec.rbegin()
  vec.crbegin()

- vec.end()
  vec.cend()
  vec.rend()
  vec.crend()

# element access

- vec[idx]
- vec.at(idx)
- vec.front()
- vec.back()

# capacity

- vec.empty()
- vec.size()

# modifiers

- vec.clear()

- vec.erase(it)
  vec.erase(it_f, it_l)

- vec.insert(it, iList)
  vec.insert(it, cnt, val)
  vec.insert(it, it_f, it_l)

- vec.push_back(val)
  vec.pop_back()
```

</details>

<details>
<summary>deque</summary>

```
#

- deque<T> dqe iList
  deque<T> dqe (cnt, val)
  deque<T> dqe (other_dqe)
  deque<T> dqe (it_f, it_l)

- dqe.assign(iList)
  dqe.assign(cnt, val)
  dqe.assign(other_dqe)
  dqe.assign(it_f, it_l)

- dqe = iList
  dqe = other_dqe
  
# random access iterator

- vec.begin()
  vec.cbegin()
  vec.rbegin()
  vec.crbegin()

- vec.end()
  vec.cend()
  vec.rend()
  vec.crend()

# element access

- dqe[idx]
- dqe.at(idx)
- dqe.front()
- dqe.back()

# capacity

- dqe.empty()
- dqe.size()

# modifiers

- dqe.clear()

- dqe.erase(it)
  dqe.erase(it_f, it_l)

- dqe.insert(it, iList)
  dqe.insert(it, cnt, val)
  dqe.insert(it, it_f, it_l)

- dqe.push_front(val)
  dqe.pop_front()
  dqe.push_back(val)
  dqe.pop_back()
```

</details>

<details>
<summary>forward_list</summary>

```
#

- forward_list<T> lst iList
  forward_list<T> lst (cnt, val)
  forward_list<T> lst (other_lst)
  forward_list<T> lst (it_f, it_l)

- lst.assign(iList)
  lst.assign(cnt, val)
  lst.assign(other_lst)
  lst.assign(it_f, it_l)

- lst = iList
  lst = other_lst

# forward iterator

- lst.before_begin()
  lst.cbefore_begin()

- lst.begin()
  lst.cbegin()

- lst.end()
  lst.cend()

# capacity

- lst.empty()

# modifiers

- lst.clear()

- lst.erase_after(it)
  lst.erase_after(it_f, it_l) // erase from (it_f, it_l)

- lst.insert_after(it, iList)
  lst.insert_after(it, cnt, val)
  lst.insert_after(it, it_f, it_l) // insert from [it_f, it_l)

- lst.push_front(val)
  lst.pop_front()
```

</details>

<details>
<summary>list</summary>

```
#

- list<T> lst iList
  list<T> lst (cnt, val)
  list<T> lst (other_lst)
  list<T> lst (it_f, it_l)

- lst.assign(iList)
  lst.assign(cnt, val)
  lst.assign(other_lst)
  lst.assign(it_f, it_l)

- lst = iList
  lst = other_lst

# bidirectional iterator

- lst.begin()
  lst.cbegin()
  lst.rbegin()
  lst.crbegin()

- lst.end()
  lst.cend()
  lst.rendn()
  lst.crend()

# capacity

- lst.empty()
- lst.size()

# modifiers

- lst.clear()

- lst.erase(it) // erase at 'it'
  lst.erase(it_f, it_l) // range [it_f it_l)

- lst.insert(it, iList)
  lst.insert(it, cnt, val)
  lst.insert(it, it_f, it_l) // range [it_f itl)

- lst.push_front(val)
  lst.pop_front()
  lst.push_back(val)
  lst.pop_back()
```

</details>

#### associative

<details>
<summary>set</summary>

```
- Collection of unique keys, sorted by keys.
- search, removal, and insertion operations have logarithmic complexity.

#
  
  cmp = greater<T>
        less<T>

- set<T> st iList
  set<T> st (other_st)
  set<T> st (it_f, it_l)

- st = iList
  st = other_st

# bidirectional iterator

- st.begin()
  st.cbegin()
  st.rbegin()
  st.crbegin()

- st.end()
  st.cend()
  st.rend()
  st.crend()

# capacity

- st.empty()
- st.size()

# modifiers

- st.clear()

- st.erase(key)
  st.erase(it)
  st.erase(it_f, it_l)

- st.insert(iList)
  st.insert(it_f, it_l)

# lookup

- st.count(key) // returns 0 or 1
- st.find(key) // returns st.end() if not found
```

</details>

<details>
<summary>multiset</summary>

```
- Collection of keys, sorted by keys.
- search, removal, and insertion operations have logarithmic complexity.

#
  
  cmp = greater<T>
        less<T>

- multiset<T> st iList
  multiset<T> st (other_st)
  multiset<T> st (it_f, it_l)

- st = iList
  st = other_st

# bidirectional iterator

- st.begin()
  st.cbegin()
  st.rbegin()
  st.crbegin()

- st.end()
  st.cend()
  st.rend()
  st.crend()

# capacity

- st.empty()
- st.size()

# modifiers

- st.clear()

- st.erase(key) // remove all occurences of key
  st.erase(it)
  st.erase(it_f, it_l)

- st.insert(iList)
  st.insert(it_f, it_l)

# lookup

- st.count(key)
- st.find(key) // returns st.end() if not found
```

</details>

<details>
<summary>map</summary>

```
- Collection of unique keys mapped to values as pair, sorted by keys.
- search, removal, and insertion operations have logarithmic complexity.

#
  
  cmp = greater<T>
        less<T>

- map<T> mp iList
  map<T> mp (other_mp)
  map<T> mp (it_f, it_l)

- mp = iList
  mp = other_mp

# bidirectional iterator

- mp.begin()
  mp.cbegin()
  mp.rbegin()
  mp.crbegin()

- mp.end()
  mp.cend()
  mp.rend()
  mp.crend()

# element access

- mp[key]
- mp.at(key)

# capacity

- mp.empty()
- mp.size()

# modifiers

- mp.clear()

- mp.erase(key)
  mp.erase(it)
  mp.erase(it_f, it_l)

// if key was already present
// val is not updated
- mp.insert(iList)
  mp.insert(it_f, it_l)

// if key was already present
// val is updated
- mp.insert_or_assign(key, val)

# lookup

- mp.count(key) // returns 0 or 1
- mp.find(key) // returns mp.end() if not found
```

</details>

<details>
<summary>multimap</summary>

```
- Collection of unique keys mapped to values as pair, sorted by keys.
- search, removal, and insertion operations have logarithmic complexity.

#
  
  cmp = greater<T>
        less<T>

- multimap<T> mp iList
  multimap<T> mp (other_mp)
  multimap<T> mp (it_f, it_l)

- mp = iList
  mp = other_mp

# bidirectional iterator

- mp.begin()
  mp.cbegin()
  mp.rbegin()
  mp.crbegin()

- mp.end()
  mp.cend()
  mp.rend()
  mp.crend()

# capacity

- mp.empty()
- mp.size()

# modifiers

- mp.clear()

- mp.erase(key) // remove all occurences of key
  mp.erase(it)
  mp.erase(it_f, it_l)

- mp.insert(iList)
  mp.insert(it_f, it_l)

# lookup

- mp.count(key)
- mp.find(key) // returns mp.end() if not found
```

</details>

#### unordered associative

<details>
<summary>unordered_set</summary>

```
- Collection of unique keys, unsorted.
- search, removal, and insertion operations have average constant-time complexity.

#

- unordered_set<T> st iList
  unordered_set<T> st (other_st)
  unordered_set<T> st (it_f, it_l)

- st = iList
  st = other_st

# forward iterator

- st.begin()
  st.cbegin()

- st.end()
  st.cend()

# capacity

- st.empty()
- st.size()

# modifiers

- st.clear()

- st.erase(key)
  st.erase(it)
  st.erase(it_f, it_l)

- st.insert(iList)
  st.insert(it_f, it_l)

# lookup

- st.count(key) // returns 0 or 1
- st.find(key) // returns st.end() if not found
```

</details>

<details>
<summary>unordered_multiset</summary>

```
- Collection of keys, unsorted.
- search, removal, and insertion operations have average constant-time complexity.

#

- unordered_multiset<T> st iList
  unordered_multiset<T> st (other_st)
  unordered_multiset<T> st (it_f, it_l)

- st = iList
  st = other_st

# forward iterator

- st.begin()
  st.cbegin()

- st.end()
  st.cend()

# capacity

- st.empty()
- st.size()

# modifiers

- st.clear()

- st.erase(key) // remove all occurences of key
  st.erase(it)
  st.erase(it_f, it_l)

- st.insert(iList)
  st.insert(it_f, it_l)

# lookup

- st.count(key)
- st.find(key) // returns st.end() if not found
```

</details>

<details>
<summary>unordered_map</summary>

```
- Collection of unique keys mapped to values as pair, unsorted.
- search, removal, and insertion operations have average constant-time complexity.

#
  
- unordered_map<T> mp iList
  unordered_map<T> mp (other_mp)
  unordered_map<T> mp (it_f, it_l)

- mp = iList
  mp = other_mp

# forward iterator

- mp.begin()
  mp.cbegin()

- mp.end()
  mp.cend()

# element access

- mp[key]
- mp.at(key)

# capacity

- mp.empty()
- mp.size()

# modifiers

- mp.clear()

- mp.erase(key)
  mp.erase(it)
  mp.erase(it_f, it_l)

// if key was already present
// val is not updated
- mp.insert(iList)
  mp.insert(it_f, it_l)

// if key was already present
// val is updated
- mp.insert_or_assign(key, val)

# lookup

- mp.count(key) // returns 0 or 1
- mp.find(key) // returns mp.end() if not found
```

</details>

<details>
<summary>unordered_multimap</summary>

```
- Collection of keys mapped to values as pair, unsorted.
- search, removal, and insertion operations have average constant-time complexity.

#

- multimap<T> mp iList
  multimap<T> mp (other_mp)
  multimap<T> mp (it_f, it_l)

- mp = iList
  mp = other_mp

# forward iterator

- mp.begin()
  mp.cbegin()

- mp.end()
  mp.cend()

# capacity

- mp.empty()
- mp.size()

# modifiers

- mp.clear()

- mp.erase(key) // remove all occurences of key
  mp.erase(it)
  mp.erase(it_f, it_l)

- mp.insert(iList)
  mp.insert(it_f, it_l)

# lookup

- mp.count(key)
- mp.find(key) // returns mp.end() if not found
```

</details>

#### adaptors

<details>
<summary>stack</summary>

```
- LIFO data structure

#
  container<T> = deque<T> // default
                 vector<T>
                 list<T>

- stack<T, container<T>> stk (container)
  stack<T> stk (other_stk)

- stk = other_stk;

# element access

- stk.top()

# capacity

- stk.empty()
- stk.size()

# modifiers

- stk.push(val)
- stk.pop()
```

</details>

<details>
<summary>queue</summary>

```
- FIFO data structure

#
  container<T> = deque<T> // default
                 list<T>

- queue<T, container<T>> que (container)
  queue<T> que (other_que)

- que = other_que;

# element access

- que.front()
- que.back()

# capacity

- que.empty()
- que.size()

# modifiers

- que.push(val)
- que.pop()
```

</details>

<details>
<summary>priority_queue</summary>

```
- a sorted stack

#
  container<T> = deque<T>
                 vector<T> // default

  cmp = greater<T>
        less<T> // default

- priority_queue<T, container<T>, cmp> que (it_f, it_l)
  priority_queue<T> que (other_que)

- que = other_que;

# element access

- que.top()

# capacity

- que.empty()
- que.size()

# modifiers

- que.push(val)
- que.pop()
```

</details>