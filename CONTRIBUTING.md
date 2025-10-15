# Contributing to RCE Engine

First off, thank you for considering contributing to RCE Engine! It's people like you that make open source great.

## How Can I Contribute?

There are many ways to contribute, from writing tutorials or blog posts, improving the documentation, submitting bug reports and feature requests or writing code which can be incorporated into RCE Engine itself.

### Reporting Bugs

-   **Ensure the bug was not already reported** by searching on GitHub under [Issues](https://github.com/arya2004/rce-engine/issues).
-   If you're unable to find an open issue addressing the problem, [open a new one](https://github.com/arya2004/rce-engine/issues/new). Be sure to include a **title and clear description**, as much relevant information as possible, and a **code sample** or an **executable test case** demonstrating the expected behavior that is not occurring.

### Suggesting Enhancements

-   Open a new issue to discuss your enhancement.
-   Clearly describe the enhancement and the motivation for it.

### Pull Requests

1.  Fork the repository and create your branch from `main`.
2.  If you've added code that should be tested, add tests.
3.  If you've changed APIs, update the documentation.
4.  Ensure the test suite passes.
5.  Make sure your code lints.
6.  Issue that pull request!

## Development

### Local Development

1.  Fork the repository.
2.  Clone your forked repository:
    ```bash
    git clone https://github.com/YOUR_USERNAME/rce-engine.git
    ```
3.  Install Go dependencies:
    ```bash
    go mod tidy
    ```
4.  Run the application:
    ```bash
    go run main.go run standalone
    ```

### Code Style

We follow the standard Go formatting and linting guidelines. Please run `go fmt` and `go vet` on your code before submitting a pull request.

## Any other questions?

Feel free to open an issue if you have any other questions.

Thank you for your contribution!
