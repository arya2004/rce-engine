# RCE Engine

A simple remote code execution engine powered by [Tork](https://github.com/runabol/tork). It allows you to execute code snippets in various languages via a simple REST API.

## Features

- Execute code in multiple languages.
- Simple JSON-based API.
- Powered by the robust Tork workflow engine for task management.

## How it Works

The engine exposes a single API endpoint `/execute`. When it receives a POST request with a JSON payload containing `code` and `language`, it performs the following steps:

1.  It creates a [Tork](https://github.com/runabol/tork) task to execute the code.
2.  The task is submitted to the Tork engine.
3.  The engine waits for the task to complete.
4.  The output (or error) of the code execution is returned as the HTTP response.

## Getting Started

### Prerequisites

- Go (version 1.18 or higher)
- A running Tork instance (this engine runs as a Tork standalone process)

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/arya2004/rce-engine.git
    cd rce-engine
    ```

2.  Install dependencies:
    ```bash
    go mod tidy
    ```

### Configuration

The `config.toml` file is used to configure the Tork engine. By default, it exposes only the `/health` and the custom `/execute` endpoints.

```toml
[coordinator.api]
endpoints.health = true
endpoints.jobs = false
endpoints.tasks = false
endpoints.nodes = false
endpoints.queues = false
endpoints.metrics = false
```

### Running the Server

To start the engine, run the following command. This will start a standalone Tork instance with the custom `/execute` endpoint enabled.

```bash
go run main.go run standalone
```

The server will start on the default Tork port (usually `8000`).

## API Endpoint

### `POST /execute`

Executes a code snippet.

**Request Body:**

```json
{
  "code": "your code here",
  "language": "language_identifier"
}
```

-   `code` (string, required): The source code to execute.
-   `language` (string, required): The programming language of the code. The supported languages depend on the Docker images used by the Tork tasks. Common identifiers include `python`, `javascript`, `go`, `ruby`, etc.

**Success Response (200 OK):**

The body of the response will contain the standard output of the executed code.

**Error Response (400 Bad Request):**

If there is an error in the request or during code execution, the response body will contain an error message.

## Example Usage

Here is an example of how to execute a Python code snippet using `curl`.

```bash
curl -X POST http://localhost:8000/execute \
-H "Content-Type: application/json" \
-d '{
  "code": "print(\"Hello from Python!\")",
  "language": "python"
}'
```

**Output:**

```
Hello from Python!
```

## License

This project is licensed under the terms of the LICENSE file.
