# Node.js Server Unresponsiveness Under Load

This repository demonstrates a common issue in Node.js where a server becomes unresponsive under heavy load.  The provided `server.js` file contains a simple HTTP server that eventually stops responding to requests without explicitly crashing.  The `serverSolution.js` file offers a solution using clustering to improve server performance and responsiveness.

## Problem

The `server.js` file creates a basic HTTP server. While it initially responds to requests, it becomes unresponsive after a significant number of concurrent requests. This is due to Node.js's single-threaded nature.  A long-running request or operation can block the event loop, preventing it from processing other requests.

## Solution

The `serverSolution.js` addresses this limitation by employing Node.js's cluster module. This allows us to create multiple worker processes, each handling a subset of incoming requests.  This distributes the load and prevents a single slow request from impacting overall server responsiveness.

## How to Run

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `npm install` to install the necessary dependencies (none for this example, but good practice).
4. Run `node server.js` to start the original, flawed server.
5. Run `node serverSolution.js` to start the improved, clustered server.

Test the servers using tools like `wrk` or `ab` to simulate concurrent requests and observe the difference in behaviour under load.