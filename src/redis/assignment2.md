# Assignment 2


## Getting Started:
  * Read the README.md file in the redis directory
  * You do not need the redis-server or redis-cli commands as described in your text.
  * Simply start with ./up.bash and ./shell.bash, this will put you into the Redis prompt.

## Day 1
1. (10 points) Read Day 1. Skip section on Unions on page 270. Work through the examples in the text. Save your database to dump.rdb (see README.md).


2. (1 point) What is the URL to Redis' documentation on its commands:
```
    https://redis.io/docs/latest/
```

3. (1 point) What is the runtime complexity (in Big-O notation) for LREM?
```
Runtime Complexity : O(N)

Details:
For removing elements from redis we need to traverse it just like a list in python which is N in worst case when we find the occurence of the element then it take M time to remove the element.
So it is O(N+M) = O(N)  // Ignore the smallest values while calculating the Big O notation.

Sources:
https://redis.io/docs/latest/commands/lrem/

```

4. (2 points) Create a structure to hold the value of your address with the key of your first name. For instance, mine would be “heidi”  “CS & IT Department, Herman Hall 207C, Western New England University, Springfield, MA, 01119”. Use the proper Redis command to show that the data has correctly been entered and followed by the results. Show both commands below including the prompts:
```
SET alyan "62 Massachusetts Ave. Springfield, MA, 01119"

GET alyan
```

5. (2 points) Create a hash structure to hold your WNE user name, first name, last name, and password. Of course provide a fake password. For instance, my data would be: “he302979”, “heidi”, “ellis”, “xxxx”.  Use the proper Redis command to show that the data has correctly been entered followed by the results. Show both commands below including the command prompts:

```
HSET aa642906 username "alyanalam" firstname "alyan" lastname "alam" password "124578963"

HGETALL aa642906
```

6. (2 points) Create a hash that holds your father’s and mother’s names as separate key-value pairs. Use the proper Redis commands to show that the data has correctly been entered followed by the results. Show both commands below including the command prompt:
```
HSET parents father "Muhammad Alam" mother "Ayesha Alam"

HGETALL parents
```

7. (3 points) Use a list to:
    * Create a stack called ‘my_stack’
    * Add elements for pears, apples, peaches
    * Remove the top element
    * Display the list to check that you have removed the proper elements
    * Add oranges to the stack
    * Display the list to check that you have removed the proper elements

Show the commands below including the command prompts:
```
LPUSH my_stack pears apples peaches

LPOP my_stack

LRANGE my_stack 0 -1

LPUSH my_stack oranges

LRANGE my_stack 0 -1

```

8.  (3 points)  In class we talked about the problem with name changes. For instance. Jane Ellen Doe might change her name to Jane Ellen Doe Fitzgerald where Ellen Doe becomes Jane’s middle name. Do the following:
    * Create hashes to hold first name of "Jane", middle name of "Ellen" and last names of "Doe".
    * Use Redis’ **transactions** to modify Jane to have a middle name of “Ellen Doe” and a last name of “Fitzgerald”. Remember, we need to ensure atomicity for this action.

Write the commands below including the command prompts:

```
HSET jane first "Jane" middle "Ellen" last "Doe"

HGETALL jane

MULTI
HSET jane middle "Ellen Doe"
HSET jane last "Fitzgerald"
EXEC

HGETALL jane

```

9. (2 points) Create a sorted set that holds the costs of the following items:  Cheetos: $2.99, apple: $1.00, Hershey’s: $3.45, and Coke: $1.79.  Print the set in ascending order.  Reduce the price of Hersheys by $1.00 using the ZINCRBY command. Print the set again in ascending order. Show the Redis commands below including the command prompts:
```
ZADD store 2.99 "Cheetos" 1.00 "apple" 3.45 "Hersheys" 1.79 "Coke"

ZRANGE store 0 -1 WITHSCORES

ZINCRBY store -1.00 "Hersheys"

ZRANGE store 0 -1 WITHSCORES

```

10. (2 points) When using 2-factor authentication, many web sites send the user a link to confirm their identity. These links typically expire within 5 minutes. Reproduce this concept in Redis by storing a key named 'link' whose value is a URL (your choice), that expires in 5 minutes. Do it in a single command. Check to ensure that the link exists. Write the commands below including the command prompts:
```
SETEX link 300 "https://www.linkedin.com/feed/"

EXISTS link
```

## Day 2

1. Read the following sections in Day 2. You do not have to "do" them. Just read and study them and know them for the exam. There is nothing to turn in for Day 2.

* Publish-subscribe
* Durability
* Snapshotting
* Append-Only File
* Security
* Master-Slave Replication

## Day 3 - Skip

Submission
1. The following files should contain all your work for this assignment:
    * assignment2.md
    * dump.rdb

 * All work must be committed to your individual GitHub repo to be considered submitted.
 * Confirm your submission by opening your repository in GitHub.
