# Go Advanced Admin

**Building the next generation of admin panels in Go**

## About Us

Go Advanced Admin is a GitHub organization dedicated to developing an advanced, extensible, and easy-to-use admin panel framework for Go (Golang). Our mission is to simplify the process of creating powerful administrative interfaces for Go applications, enabling developers to manage their applications effectively and efficiently.

Our primary codebase is located at [github.com/go-advanced-admin/admin](https://github.com/go-advanced-admin/admin). This repository serves as the core of our framework, providing the foundational components and abstractions necessary to build robust admin panels.

In addition to the core library, we maintain several repositories that offer integrations with popular ORMs and web frameworks, ensuring seamless integration with your existing Go projects.

## Repositories

- **Core Library**:
  - [admin](https://github.com/go-advanced-admin/admin): The core library that provides the foundational components for building advanced admin panels in Go.

- **ORM Integrations**:
  - [orm-gorm](https://github.com/go-advanced-admin/orm-gorm): Integration with GORM, the popular ORM library for Go.

- **Web Framework Integrations**:
  - [web-echo](https://github.com/go-advanced-admin/web-echo): Integration with Echo, a high-performance, minimalist Go web framework.

## Project Status

**Note:** This project is currently under active development and is not yet ready for production use. We are working diligently to build a stable and feature-rich framework. We appreciate your patience and welcome any contributions or feedback.

## Getting Started

To get started with Go Advanced Admin, you can include the core library and any necessary integrations based on your stack. Please refer to the documentation in each repository for installation instructions and usage examples.

**Example:**

Here's a basic example of setting up the admin panel using the core library and integrating it with GORM and Echo:

```go
// main.go

package main

import (
    "github.com/glebarez/sqlite"
    "github.com/go-advanced-admin/admin"
    "github.com/go-advanced-admin/orm-gorm"
    "github.com/go-advanced-admin/web-echo"
    "github.com/labstack/echo/v4"
    "gorm.io/gorm"
    // ... other imports
)

func main() {
    e := echo.New()
    web := adminecho.NewIntegrator(e.Group(""))

    permissionFunc := func(req admin.PermissionRequest, ctx interface{}) (bool, error) {
        return true, nil // Implement your permission logic here
    }

    db, err := gorm.Open(sqlite.Open(":memory:"), &gorm.Config{})
    if err != nil {
        log.Fatalf("Failed to connect database: %v", err)
    }

    orm := admingorm.NewIntegrator(db)

    panel, err := admin.NewPanel(orm, web, permissionFunc, nil)
    if err != nil {
        log.Fatal(err)
    }

    // Register apps and models
    // ...

    e.Logger.Fatal(e.Start(":8080"))
}
```

*Please refer to the documentation for detailed setup instructions and examples.*

## Contributing

We welcome contributions from the community! Whether you're reporting bugs, suggesting new features, improving documentation, or submitting pull requests, your input helps us improve and grow the project.

To contribute:

1. **Fork** the repository you want to contribute to.
2. **Create a new branch** for your feature or bugfix.
3. **Commit** your changes with clear and descriptive commit messages.
4. **Push** your branch to your fork.
5. **Open a pull request** against the `main` branch of the original repository.

Before contributing, please read our [Contributing Guidelines](https://github.com/go-advanced-admin/admin/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/go-advanced-admin/admin/blob/main/CODE_OF_CONDUCT.md).

## License

Go Advanced Admin is released under the MIT License. See the [LICENSE](https://github.com/go-advanced-admin/admin/blob/main/LICENSE) file for details.

## Contact

If you have any questions, suggestions, or need assistance, feel free to open an issue in the relevant repository or contact us via email at [contact@example.com].

---

We look forward to building an amazing admin panel framework with your help!
