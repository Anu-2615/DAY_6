# DAY_6
TWO QUESTION_ REMOVED LINKED LIST &amp; HAPPY_NUMBER
# Remove Linked List Elements (LeetCode 203)

## Problem Statement
Given the head of a linked list and an integer `val`, remove all the nodes of the linked list that have `Node.val == val`, and return the new head.

## Example
**Input:** head = [1,2,6,3,4,5,6], val = 6  
**Output:** [1,2,3,4,5]

## Approach
We use a **dummy node** to simplify the removal process, especially if the head node itself needs to be removed. Then, we traverse the list and skip all nodes that match the target value.

## Java Code

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if (head == null) {
            return head;
        }

        ListNode dummy = new ListNode(0); // Create a dummy node
        dummy.next = head;
        ListNode temp = dummy;

        while (temp.next != null) {
            if (temp.next.val == val) {
                temp.next = temp.next.next; // Skip the node
            } else {
                temp = temp.next; // Move to next node
            }
        }

        return dummy.next;
    }
}
Why Use a Dummy Node?
Simplifies edge cases (e.g., when head node needs to be deleted)

Ensures we always have a reference to the start of the list

Time Complexity
O(n) — We traverse the entire list once.

Space Complexity
O(1) — We only use constant extra space.











# 💡 LeetCode 202 - Happy Number

## 📘 Problem Statement

Write an algorithm to determine if a number `n` is a **happy number**.

A **happy number** is defined using the following process:

- Starting with any positive integer, replace the number by the **sum of the squares of its digits**.
- Repeat the process until the number either **equals 1** (where it will stay), or **enters a cycle** that does not include 1.
- Numbers for which this process **ends in 1** are called **happy numbers**.

### ✅ Return
`true` if `n` is a happy number, and `false` if not.

---

## 📥 Example

### Example 1:
```text
Input: n = 19
Output: true
Explanation:
1² + 9² = 82  
8² + 2² = 68  
6² + 8² = 100  
1² + 0² + 0² = 1

Input: n = 2
Output: false
public boolean isHappy(int n) {
    int sum = 0;
    int temp = n;

    while (n > 9) {
        while (temp > 0) {
            int rem = temp % 10;
            sum += rem * rem;
            temp = temp / 10;
        }

        n = sum;
        temp = sum;
        sum = 0;
    }

    return (n == 1 || n == 7);
}

