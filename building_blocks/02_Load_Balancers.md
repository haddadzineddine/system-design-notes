## Load Balancers

Load balancers distribute incoming client requests evenly across multiple servers, improving availability, fault tolerance, and scalability.

#### Key Functions:
- **Request Distribution:** Balances load fairly among servers to prevent overload.
- **Health Checks:** Detects and bypasses failed or unhealthy servers.
- **Session Persistence:** Ensures requests from the same client go to the same server when needed.
- **SSL Termination:** Handles TLS/SSL encryption to offload processing from backend servers.

#### Load Balancing Algorithms:
- **Round Robin:** Requests sent sequentially to each server.
- **Least Connections:** Routes requests to the server with the fewest active connections.
- **IP Hash:** Uses client IP address to consistently route requests to the same server.
- **Weighted:** Distributes requests based on server capacity or priority.