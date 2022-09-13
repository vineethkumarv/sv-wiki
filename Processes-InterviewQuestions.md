### 1.Difference between fork_join,fork_join_any and fork_join_none ?
|   **fork_join**  |          **fork_join_any**                         |                    **fok_join_none**                |                    
|:---------------|:------------------------------|:------------------------|
|In fork_join the main threads will execute after all the threads in the fork_join is executed|In fork_join_any the main threads executes if any one of the child threads excecutes | In fork_join_none child threads and main threads are executed parallely |
| <img width="122" alt="fork-join  " src="https://user-images.githubusercontent.com/110509375/189809970-21ee4efe-78b7-4974-99ae-7471c4a56df4.png">|   <img width="116" alt="fork_join_any" src="https://user-images.githubusercontent.com/110509375/189810277-5c297e3c-97f7-406f-b7bf-115694df24cd.png">|<img width="130" alt="fork-join_none" src="https://user-images.githubusercontent.com/110509375/189810446-361a0b82-1f33-4f2c-bf91-f0da2b0893c3.png">|

### 2.Can we use wait_fork in fork_join ?
We know that the main thread is executed only when all the threads in fork_join is executed so here no need of using wait_fork. But  you can use fork - join_none or join_any, then you can use wait fork after the join_join_any or fork_join_none  statement to wait for all the threads in the fork-join_any or fork_join_none to complete.