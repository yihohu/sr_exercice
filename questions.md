# Data Science Exercice
#### Question 3

With peers sending such datastructure and our _backend_ server making such operations, we retrieve exactly **all** the connection durations on the network at the moment of the snapshot and we are able to plot the _exact distribution_ of the connection durations.
`question2.py` main has several simulations with increasing numbers of peers and peer pool size. Run the simulations with your implementation. What do you see? Can you explain the limitations of the implementations of question 2 taking into account that a _real_ peer network can have _millions_ of peers? (answer below in this file)
> From the results in question2, when each peer has limited connections, the increase of cost of backend calculation is mostly related to number of peers. 
> But when connections limit is increased, server calculation cost increase is not proportional to the number of connection limit. 
> This is because that for n peers, there are n * (n - 1) / 2 connections. 
> Another problem in this approach is that all connections are calculated 2 times

#### Question 4nb.ipynb

Go to the file `question4.py`:
Propose new implementations of `send_data_to_backend` and `process_backend_data` that can deal with millions of peers _and_ still provide a good representation of the _distribution_ of the connection duration. You are free to add any written comments, add pictures etc. to enhance your answer.
> In previous approach, all the data processing work is centralized in backend server. When there are millions of peers, the number of connections will increase dramatically. 
> And This generates too much data to process for the server. But actually histogram itself can be a nice way to store the data distribution in a limited size and at the same time keep enough level of precision in data distribution.
> This approach in q4 is more distributed, each peer should calculate its own connection histogram and sends only histogram to server. And the server should only work on accumulating the results from all the peers.
> In this way, the server delegates a majority of calculation task to peers. And its calculation cost is proportional only to number of peers.

