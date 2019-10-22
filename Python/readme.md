
# 推薦影片
```
微軟　Python for Beginners
每節課五分鐘，微軟推出Python短視頻入門課，上Github榜首
Channel 9 Python for Beginners course


https://channel9.msdn.com/Series/Intro-to-Python-Development?WT.mc_id=python-c9-niner

簡報與示範程式:microsoft/c9-python-getting-started
https://github.com/microsoft/c9-python-getting-started
```

# The Algorithms - Python

```
https://github.com/TheAlgorithms/Python
```
### 範例學習1
```
# https://github.com/TheAlgorithms/Python/blob/master/backtracking/all_combinations.py
# -*- coding: utf-8 -*-

"""
	In this problem, we want to determine all possible combinations of k
	numbers out of 1 ... n. We use backtracking to solve this problem.
	Time complexity: O(C(n,k)) which is O(n choose k) = O((n!/(k! * (n - k)!)))
"""


def generate_all_combinations(n: int, k: int) -> [[int]]:
    """
    >>> generate_all_combinations(n=4, k=2)
    [[1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]]
    """

    result = []
    create_all_state(1, n, k, [], result)
    return result


def create_all_state(increment, total_number, level, current_list, total_list):
    if level == 0:
        total_list.append(current_list[:])
        return

    for i in range(increment, total_number - level + 2):
        current_list.append(i)
        create_all_state(i + 1, total_number, level - 1, current_list, total_list)
        current_list.pop()


def print_all_state(total_list):
    for i in total_list:
        print(*i)


if __name__ == "__main__":
    n = 4
    k = 2
    total_list = generate_all_combinations(n, k)
    print_all_state(total_list)
```

### 範例學習2

```
# https://github.com/TheAlgorithms/Python/blob/master/backtracking/all_permutations.py

"""
	In this problem, we want to determine all possible permutations
	of the given sequence. We use backtracking to solve this problem.
	Time complexity: O(n! * n),
	where n denotes the length of the given sequence.
"""


def generate_all_permutations(sequence):
    create_state_space_tree(sequence, [], 0, [0 for i in range(len(sequence))])


def create_state_space_tree(sequence, current_sequence, index, index_used):
    """
	Creates a state space tree to iterate through each branch using DFS.
	We know that each state has exactly len(sequence) - index children.
	It terminates when it reaches the end of the given sequence.
	"""

    if index == len(sequence):
        print(current_sequence)
        return

    for i in range(len(sequence)):
        if not index_used[i]:
            current_sequence.append(sequence[i])
            index_used[i] = True
            create_state_space_tree(sequence, current_sequence, index + 1, index_used)
            current_sequence.pop()
            index_used[i] = False


"""
remove the comment to take an input from the user 
print("Enter the elements")
sequence = list(map(int, input().split()))
"""

sequence = [3, 1, 2, 4]
generate_all_permutations(sequence)

sequence = ["A", "B", "C"]
generate_all_permutations(sequence)
```
