# http_server_demo_yo

A simple HTTP/1.1 server written in the [Yo programming language](https://github.com/nicolo-ribaudo/yo-lang).

## Features

- **Async I/O** — Uses `io.await` with `IO` algebraic effect for non-blocking TCP networking
- **Algebraic effects** — `Exception` effect for structured error handling (per-connection error isolation)
- **HTTP parsing** — Hand-written HTTP/1.1 request parser (method, path, headers, body)
- **Routing** — Simple path-based router with multiple response types

### Routes

| Path | Description |
|------|-------------|
| `/` | HTML welcome page with links to other routes |
| `/hello` | Plain text `Hello, World!` |
| `/json` | JSON response with language info |
| `/echo` | Echo back request method, path, and headers as HTML |
| `*` | 404 Not Found |

## Build & Run

```bash
yo build
./yo-out/bin/http_server_demo_yo
```

Then visit <http://localhost:8080> or test with curl:

```bash
curl http://localhost:8080/
curl http://localhost:8080/hello
curl http://localhost:8080/json
curl -H "X-Custom: test" http://localhost:8080/echo
```

## Project Structure

```
http_server_demo_yo/
├── build.yo          # Build configuration
├── src/
│   └── main.yo       # HTTP server implementation (~250 lines)
└── README.md
```

## Yo Language Features Demonstrated

- `async/await` via the `IO` effect and `io.await`
- Algebraic effects with `given`/`Exception`/`escape` for error handling
- TCP server with `TcpListener.bind`, `listener.accept`, `stream.read/write`
- String processing with `split`, `index_of`, `substring`, `trim`
- Pattern matching with `match` and `cond`
- `while runtime(true)` for infinite accept loops
- Template strings for HTML/JSON response building
