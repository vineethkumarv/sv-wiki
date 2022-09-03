# Choosing an arrays:

## Fixed Arrays/Static Arrays:

**1) Fixed Arrays Over All Arrays:**

* Fixed Arrays execute faster than all other types of arrays (i.e Associative arrays, dynamic arrays, queues) because it will store in uninitialized data segment (bss segment) of memory. and so it will consume less simulation time to execute. it will show in below figure.

![memory_segments](https://user-images.githubusercontent.com/110448056/188258335-c478ebd9-4785-415d-9873-cbf6269eecd4.png)

                                                Figure.1. Memory Layout

* Size is known previously then we can choose fixed arrays over all other types of arrays.

## Dynamic Arrays:

**1) Dynamic Arrays Over Fixed Arrays:**

* Memories allocated at run time so memory will not be wasted but in fixed array memories would be wasted.
* We can easily add elements using new() method but in fixed arrays we can't add elements after the declaration.
* We can delete entire arrays after allocating the memories to it but in fixed arrays we can't delete the memories after declaring array.

**2) Dynamic Arrays Over Associative Arrays:**

* Indexing is in continues manner but in associative arrays it's non continuous. it's show in below figure.

![indexing](https://user-images.githubusercontent.com/110448056/188263690-151e9f91-36a8-4b2e-baf6-42505a1f7fc1.png)

                                 Figure.2. continuous and non continuous indexing

* We can find relation between indexing so travelling through arrays with ease using loops but in associative arrays keys are required.

**3) Dynamic Arrays Over Queues:**

* It's faster in execution and it will required less simulation time but queues will required more time to execute so dynamic arrays are faster in execution.
