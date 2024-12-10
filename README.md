# Express.js Server Hangs After Long-Running Operation

This repository demonstrates a common issue in Express.js applications where the server appears to hang or become unresponsive after initiating a long-running operation, such as a database query or a complex calculation.  The problem stems from the synchronous nature of `res.send()` which blocks subsequent requests.

## Reproducing the Bug

1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install` to install the required dependencies.
4. Run `node bug.js` to start the server.
5. Make a request to `http://localhost:3000/`.  You'll notice a 5-second delay.
6.  While this 5 second delay is ongoing, try making more requests - they will hang until the first request completes. This demonstrates the blocking nature of the issue. 

## Solution

The solution involves using asynchronous operations and appropriate middleware to handle long-running tasks without blocking the event loop. The `bugSolution.js` file demonstrates a corrected implementation utilizing `setTimeout` to simulate a long running task.