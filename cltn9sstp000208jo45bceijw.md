---
title: "Day 25: Concurrency and Parallelism (Threading, Multiprocessing) with practical"
seoTitle: "Concurrency and Parallelism (Threading, Multiprocessing) with practica"
seoDescription: "Mastering Concurrency and Parallelism in Python: Implementing Theory into Practice"
datePublished: Mon Mar 11 2024 18:21:56 GMT+0000 (Coordinated Universal Time)
cuid: cltn9sstp000208jo45bceijw
slug: day-25-concurrency-and-parallelism-threading-multiprocessing-with-practical
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710179926968/6266f51a-c1ab-4a4f-ba96-aadf2a716e2a.png
tags: python, concurrency, parallelism

---

This is the twenty-fifth blog in my Python learning journey, and it's the second one discussing Concurrency and Parallelism in Python. In the previous blog, we covered the theoretical aspects of these topics, and now we'll dive into their code implementation. I'm excited to continue exploring this subject and sharing my progress with you throughout this series.

### Concurrency

```python
import threading
import time

def print_numbers():
    for i in range(1, 6):
        print(f"Thread {threading.current_thread().name}: {i}")
        time.sleep(1)

# Create multiple threads
threads = []
for i in range(3):
    thread = threading.Thread(target=print_numbers, name=f"Thread-{i+1}")
    threads.append(thread)
    thread.start()

# Wait for all threads to finish
for thread in threads:
    thread.join()

print("All threads have finished.")
```

This code creates three threads, each printing numbers from 1 to 5 with a delay of 1 second between each number. Despite running concurrently, the output may vary due to scheduling.

### Parallelism

Here's a simple example of parallelism in Python using the `multiprocessing` module to calculate the square of numbers in parallel:

```python
import multiprocessing

def square(number):
    return number * number

if __name__ == "__main__":
    numbers = [1, 2, 3, 4, 5]

    # Create a Pool of worker processes
    with multiprocessing.Pool(processes=3) as pool:
        # Map the square function to the list of numbers
        results = pool.map(square, numbers)

    print("Original numbers:", numbers)
    print("Squared numbers:", results)
```

* We define a `square` function that takes a number and returns its square.
    
* Inside the `if __name__ == "__main__":` block (to ensure multiprocessing works correctly on Windows), we create a list of numbers.
    
* We create a `Pool` of worker processes with `multiprocessing.Pool(processes=3)`, specifying that we want to use three processes.
    
* We use the `map` function of the `Pool` object to apply the `square` function to each element in the `numbers` list. This distributes the computation of squares across multiple processes, achieving parallelism.
    
* The results are collected and stored in the `results` list.
    
* Finally, we print the original numbers and their corresponding squares.
    

### Conclusion:

In this blog, we've transitioned from theoretical discussions to practical implementations of concurrency and parallelism in Python. We explored two fundamental techniques: threading for concurrency and multiprocessing for parallelism.

With threading, we utilized the threading module to create multiple threads that executed concurrently. By defining a print\_numbers function and spawning three threads, we demonstrated how tasks can overlap in time, potentially enhancing program performance.

In parallelism, we employed the multiprocessing module to compute the square of numbers in parallel. By creating a Pool of worker processes and distributing the computation across them, we harnessed the computational power of multiple CPU cores, resulting in significant performance improvements for CPU-bound tasks.

Thankyou💕💕