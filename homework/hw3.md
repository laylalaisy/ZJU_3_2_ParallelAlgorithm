 

# Homework3 :  

## 2-Coloring
1. (40 points) Show that if an unoriented linked list can be 2 colored by an algorithm, then it can be oriented in the same time.

- Because the unoriented lined list can be orientate during color, the neighbors of each node should be different. Thus, the direction can know the next node according to different color.
- First using pointer jumping. A[i].next = A[i].next.next which A[i].next.next != A[i].

```
0 -> 2 -> 4
1 -> 3 -> 5
```

- Then color then with 2 colors, each node has different color to its neighbor.

```
0 -> 2 -> 4            （1）
R    G    R

1 -> 3 -> 5            （2）
R    G    R

0 -> 1 -> 2 -> 3 -> 4 -> 5
R         G         R                     （1）
     R         G         R                （2）
```

- Orientate the linked list.
  - Node in group(1), if its color is R, then the next node should be color R.
  - Node in group(1), if its color is G, then the next node should be color G.
  - Node in group(2), if its color is R, then the next node should be color G.
  - Node in group(2), if its color is G, then the next node should be color R.

 

2. (50 points) Show that if a linked list can be oriented by an algorithm, then it can be 2 colored in the same time. 
```
0 -> 1 -> 2 -> 3 -> 4 -> 5
```
- Use pointer jumping. If a linked list is already oriented by an algorithm, then we already know the direction and the next node of each node. Thus, we could create two linked list using pointer jumping.

```
0 -> 2 -> 4
1 -> 3 -> 5
```

- For the last node if its next node exist and its next.next node does not exist. Then link this node with its next node and combine as a new linked list.

```
0 -> 2 -> 4 -> 5 <- 3 <- 1
```

- Use the algorithm to orientate it again and get the new linked list.

```
0 -> 2 -> 4 -> 5 -> 3 -> 1
```

- Then the nodes with same direction use one color and start from the last node with different direction use another color.

```
0 -> 2 -> 4 ->    5 <- 3 <- 1
0 -> 2 -> 4 ->    5 -> 3 -> 1
```



 

## 3-Coloring Algorithm
3. (20 points) Describe the **O(nlog * n/p+log  *n)** time 3-coloring algorithms we discussed in class.
- Main Idea: 

  After one time of coloring, the left type of colors becomes 2logn of the previous type of colors. Recursively do this until the remain type of color is smaller than 10 types;

- Process:

  Number of steps: log * n;

  Time = n(log * n)/p + log * n;

 

4. (20 points) Describe the **O(nlogi/p+log(i)n+logi)** time 3-coloring algorithms we discussed in class.

|      |      |      |
| ---- | ---- | ---- |
|      |      |      |
|      |      |      |
|      |      |      |

- Coloring each node with 2log(n) colors;
- Use bucket sort to sort each node into a [log(i)] * [n/log(i)] array;
- There are two kinds of pointers, one is intra-row pointer, the other is inter-row pointer. Each col has a processor and color node which is inter-row in parallel way;
- Then deal with intra-row pointers. Move down the color as the color number to adjust those intra-row pointers as inter-row pointers;
- Then color them again;
- Time = n*log(i)/p + log(i) + log(i)n;

 

5. (20 points) How do you color a linked list with 2 colors? What is the time complexity in terms of n and p?

- Similar to last question.
- Coloring each node with 2log(n) colors;
- Use bucket sort to sort each node into a [log(i)] * [n/log(i)] array;
- Sort each col according to colors;
- Deal with intra-row pointers. Move down the color as the color number to adjust those intra-row pointers as inter-row pointers;
- Color each row in parallel and use two different colors.

 