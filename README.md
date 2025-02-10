# user-agents

This module provides an easy-to-use interface for managing and utilizing correct user agents when making HTTP requests. It ensures that the user agents used are appropriate and up-to-date, enhancing the reliability and accuracy of the requests.

## Installation

```sh
go get -u github.com/FlavioCFOliveira/user-agents
```

## Usage

Obtaining a random user agent string

```go
import (
    "github.com/FlavioCFOliveira/user-agents"
)

func main() {
    // Obtain a random User-Agent string
    randomUA := useragents.GetRandomUserAgent()

    // Print the random User-Agent string
    fmt.Println("Random User-Agent:", randomUA)
}
```

Setting The `User-Agent` Header of a http Request

```go
import (
    "github.com/FlavioCFOliveira/user-agents"
)

func main() {
     // Create a new HTTP client
    client := &http.Client{}

    // Create a new HTTP request
    req, err := http.NewRequest("GET", "https://example.com", nil)
    if err != nil {
        fmt.Println("Error creating request:", err)
        return
    }

    // Set a random User-Agent header
    useragents.SetRandomUserAgent(req)

    // Perform the HTTP request
    resp, err := client.Do(req)
    if err != nil {
        fmt.Println("Error performing request:", err)
        return
    }
    defer resp.Body.Close()

    // do something with the response
}
```

## License

This project is licensed under the BSD 3-Clause - see the [LICENSE](LICENSE) file for details.
