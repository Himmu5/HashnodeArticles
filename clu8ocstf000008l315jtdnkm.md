---
title: "Day 40: Searching algorithms with Python"
seoTitle: "Searching algorithms with Python"
seoDescription: "Navigating Data: Exploring Searching Algorithms in Python"
datePublished: Tue Mar 26 2024 17:52:33 GMT+0000 (Coordinated Universal Time)
cuid: clu8ocstf000008l315jtdnkm
slug: day-40-searching-algorithms-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711473633948/7fdc0c56-ab68-466d-a94f-08fc18d88bb6.png
tags: python, 2articles1week, binary-search-algorithm, searching-algorithms

---

Today marks the fortieth day of my Python learning series. In this blog post, I am excited to share my latest discoveries on essential searching algorithms. These algorithms play a pivotal role in virtually every project, making them a fundamental aspect of programming.

### Searching Algorithms

1. Linear Search: In linear search, we traverse elements one by one, systematically checking each element until we find the desired item.
    
    ```python
    list = [ 5 , 10 , 15, 20, 25 ]
    target = 200
    def findInList(l: list):
        for e in l:
            if(e == target):
                return True;
        return False
    print(findInList(list))
    ```
    
2. **Binary Search**: Binary search is a divide-and-conquer algorithm. It involves dividing the sorted list into two halves and then efficiently determining which half the target element resides in, narrowing down the search space until the element is found.
    
    ```python
    def binarySearch(list, target):
        start = 0;
        end = len(list)
        while(start < end):
            mid = (start + end) / 2
            mid = int(mid)
            print(mid)
            if list[mid] > target:
                end = mid - 1
            elif list[mid] < target:
                start = mid + 1
            elif list[mid] == target:
                print("index: ",mid)
                return;
    
    list = [ 5 , 10 , 15 , 20 ]
    binarySearch(list, 15)
    ```
    

These are two very important search algorithms that are very used in developing any app.

### Conclusion

  
Conclusion: This blog post explored two critical searching algorithms: Linear Search and Binary Search. Here's a concise summary:

1. **Linear Search:** This algorithm checks each element sequentially until finding the target. It's simple but less efficient for large datasets due to its linear time complexity.
    
2. **Binary Search:** Operating on sorted lists, Binary Search divides the search space in half with each iteration, resulting in logarithmic time complexity. It's highly efficient for large datasets.
    

Mastering these algorithms is crucial for optimizing data retrieval and enhancing application performance. Continued practice and exploration of algorithms are essential for skill development in programming.

Thank you💕💕