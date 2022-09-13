**1.Difference between fork_join,fork_join_any and fork_join_none ?**
|   **fork_join**  |          **fork_join_any**                         |                    **fok_join_none**                |                    
|:---------------|:------------------------------|:------------------------|
|In fork_join the main(parent) threads will execute after all the threads(child threads) in the fork_join is executed|In fork_join_any the main(parent) threads executes if any one of the child threads excecutes | In fork_join_none child threads and main(parent) threads are executed parallely |
| <img width="122" alt="fork-join  " src="https://user-images.githubusercontent.com/110509375/189809970-21ee4efe-78b7-4974-99ae-7471c4a56df4.png">|   <img width="116" alt="fork_join_any" src="https://user-images.githubusercontent.com/110509375/189810277-5c297e3c-97f7-406f-b7bf-115694df24cd.png">|<img width="130" alt="fork-join_none" src="https://user-images.githubusercontent.com/110509375/189810446-361a0b82-1f33-4f2c-bf91-f0da2b0893c3.png">|

**2.Can we use wait_fork in fork_join ?**

We know that in fork_join  the main thread is executed only when all the threads in fork_join is executed so here no need of using wait_fork.
We can use wait fork after the fork_join_any or fork_join_none  statement to wait for all the threads in the fork-join_any or fork_join_none to complete.
So here in fork_join wait_fork is not required.

**3.Difference between Blocking and Non-Blocking Assignments ?**
|**blocking** |**Non-Blocking** |
|:-------------|:----------------|
|In Blocking Assignment one statement is executed then the next statement will executed i.e first expression of right hand side is evaluated and immediately assigned to the left hand side variable|In Non-Blocking assignment evaluated all the right hand side expression for the current time unit and assigned to left-hand side variable at the end of the time unit|
|Represented by  " *=* "|Represented by " <= "|
|It executes sequentially |It executes parallely|
|Blocking is used in combinational|Non-Blocking is used in sequential|
|<img width="222" alt="b" src="https://user-images.githubusercontent.com/110509375/189822970-f52ec9ac-1f29-43a7-8185-e26a66723c09.png">|<img width="215" alt="image" src="https://user-images.githubusercontent.com/110509375/189822751-b7be6bdf-21d0-4db7-8a13-b030bdc90479.png">|
**4.Difference between wait event and @ event ?**
If we triggered wait and @ in the same delay then wait statement is executed 

 

