# CMPS 2200  Recitation 01

**Name (Team Member 1):** Jim Haines 
**Name (Team Member 2):** Lily Yee

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

The worst case value for both linear and binary search is a number that is not in
the list being searched. In this case, a key of -1 will ensure a worst case scenario because none of the lists being searched have a value of -1. 


- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

The best case value of 'key' for linear_search would be for 'key' to be the first value in the list, because linear search checks values in the order they appear in the list. 

The best case value of 'key' for binary_search would be for 'key' to be the middle value in the list. This is because binary_search first checks the middle value of the list and then splits the list at that point if the middle value is not the 'key'.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**

[(10, 0.0035762786865234375, 0.0045299530029296875),
 (100, 0.009775161743164062, 0.0045299530029296875),
 (1000, 0.11372566223144531, 0.008106231689453125),
 (10000, 2.0148754119873047, 0.010967254638671875),
 (100000, 7.189750671386719, 0.019311904907226562),
 (1000000, 72.32522964477539, 0.027179718017578125),
 (10000000, 754.4746398925781, 0.03361701965332031)]

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**

Yes, these theoretical runtimes do match our results. 

Since linear_search has a linear runtime, we expected runtimes of the function to increase approximately linearly to the input size. This is what happens as we can see in our compare_search results. Once the list size gets to be on the larger size, we can see that linear_search runtime increases by about as much as the size of the list, for example: as the list size goes from 1000000 to 10000000, the runtime is increased about 10 times, from 72.22 to 754.47 

Binary search has theoretical runtime log_2(n), which should mean that runtimes increase at a much lower rate than the size of the list being searched. We can see that this is true because binary_search runtimes stay relatively low for each list of each size. We can see that as the size of the list goes from 10 to 10000000, the runtime is only increased from .00453 to .03362, despite the 1000000 times increase of the list size.


- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**

  The worst case time complexity of a linear search of n elments k times is O(n*k) and since k is a constant, O(n) is the worst case time completity

  + For binary search? **TODO: your answer goes here**

  To sort a list takes Theta(n^2) time, and then to binary search that list k times it takes log_2(n)*k, so the worst case runtime is n^2 + log_2(n)

  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**

  It is more efficient to start using binary search when O(n) >= n^2+log_2(n). In other words, it is more efficient to start using binary search when the runtime of searching k times with linear search becomes greater than the runtime of sorting and then binary searching a list. 