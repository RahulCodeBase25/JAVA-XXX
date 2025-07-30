
# DSA Interview Prep with Test Cases (MCX India + Popular Patterns)

This `.md` file includes:
- 🔹 Top DSA questions you've practiced
- 🔹 Real MCX India coding problems
- 🔹 All solutions runnable directly from a Java `main()` method

---

## ✅ 1. Find Midpoint in Linked List

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class FindMidpoint {
    public static ListNode findMiddle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        ListNode mid = findMiddle(head);
        System.out.println("Midpoint: " + mid.val); // Output: 3
    }
}
```

---

## ✅ 2. Reverse a Singly Linked List

```java
class ReverseLinkedList {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int x) { val = x; }
    }

    public static ListNode reverseList(ListNode head) {
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }

    public static void printList(ListNode head) {
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);

        ListNode rev = reverseList(head);
        printList(rev); // Output: 3 2 1
    }
}
```

---

## ✅ 3. Remove Duplicates from Sorted Array

```java
public class RemoveDuplicatesSortedArray {
    public static int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 1, 2, 2, 3, 4};
        int len = removeDuplicates(arr);
        for (int i = 0; i < len; i++) {
            System.out.print(arr[i] + " ");
        }
        // Output: 1 2 3 4
    }
}
```

---

## ✅ 4. Kadane’s Algorithm (Max Subarray Sum)

```java
public class KadanesAlgorithm {
    public static int maxSubArray(int[] nums) {
        int maxSoFar = nums[0];
        int currentSum = nums[0];

        for (int i = 1; i < nums.length; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSoFar = Math.max(maxSoFar, currentSum);
        }

        return maxSoFar;
    }

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Max Subarray Sum: " + maxSubArray(arr)); // Output: 6
    }
}
```

---

## ✅ 5. Longest Substring Without Repeating Characters

```java
import java.util.*;

public class LongestUniqueSubstring {
    public static int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int left = 0, maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        String s = "abcabcbb";
        System.out.println("Longest unique substring length: " + lengthOfLongestSubstring(s)); // Output: 3
    }
}
```

---

## ✅ 6. Two Sum Problem

```java
import java.util.*;

public class TwoSum {
    public static int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{}; // no solution
    }

    public static void main(String[] args) {
        int[] arr = {2, 7, 11, 15};
        int target = 9;
        int[] res = twoSum(arr, target);
        System.out.println("Indexes: " + res[0] + ", " + res[1]); // Output: 0, 1
    }
}
```

---

## ✅ 7. Check if a number is Prime without using %, /, or * operators

```java
public class PrimeCheck {
    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        for (int i = 2; i < n; i++) {
            int temp = n;
            while (temp >= i) {
                temp = temp - i;
            }
            if (temp == 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println("Is 7 prime? " + isPrime(7)); // true
        System.out.println("Is 9 prime? " + isPrime(9)); // false
    }
}
```

---

## ✅ 8. Print Numbers from 1 to N Using Recursion

```java
public class PrintRecursion {
    public static void printNumbers(int n) {
        if (n == 0) return;
        printNumbers(n - 1);
        System.out.print(n + " ");
    }

    public static void main(String[] args) {
        printNumbers(5); // Output: 1 2 3 4 5
    }
}
```

---
