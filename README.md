# 🌐 42_webserv

<p align="center">
  <img src="https://img.shields.io/badge/C++-98-blue.svg? style=flat&logo=cplusplus" alt="C++98" />
  <img src="https://img.shields.io/badge/nginx-inspired-green.svg? style=flat&logo=nginx" alt="nginx-inspired" />
</p>

A lightweight yet performant **nginx-like HTTP web server** written in C++98, developed as part of the 42 School curriculum.  This project demonstrates deep understanding of network programming, HTTP protocol implementation, and concurrent I/O handling.

---

## Table of Contents
- [✨ Features](#-features)
  - [Core Functionality](#core-functionality)
  - [Configuration](#configuration)
  - [Advanced Features](#advanced-features)
  - [Architecture Highlights](#architecture-highlights)
- [🛠️ Technical Stack](#️-technical-stack)
- [📁 Project Structure](#-project-structure)
- [🚀 Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Building](#building)
  - [Running](#running)
- [⚙️ Configuration Example](#️-configuration-example)
- [🧪 Testing](#-testing)
- [📚 Skills Demonstrated](#-skills-demonstrated)
- [👥 Authors](#-authors)
- [📄 License](#-license)
- [🙏 Acknowledgments](#-acknowledgments)

---

## ✨ Features

### Core Functionality
- **HTTP/1.1 Protocol Support** - Full implementation of the HTTP/1.1 specification
- **Multiple HTTP Methods** - Supports `GET`, `POST`, `PUT`, and `DELETE` requests
- **Non-blocking I/O** - Event-driven architecture using `poll()` for high performance
- **Concurrent Connections** - Efficiently handles multiple simultaneous client connections
- **Keep-Alive Connections** - Persistent connections for improved performance

### Configuration
- **nginx-like Configuration File** - Intuitive configuration syntax inspired by nginx
- **Virtual Hosts** - Support for multiple server blocks with different configurations
- **Location Blocks** - Fine-grained control over request handling per URI path
- **Custom Error Pages** - Configurable error pages for different HTTP status codes
- **Client Body Size Limits** - Configurable request body size restrictions (B/K/M/G units)

### Advanced Features
- **CGI Support** - Execute dynamic scripts (PHP, Python, etc.) via CGI interface
- **File Uploads** - Handle multipart/form-data file uploads
- **Directory Listing** - Auto-generate directory indexes when enabled
- **URL Redirections** - Support for HTTP redirects (301, 302, etc.)
- **Cookie Handling** - Parse and manage HTTP cookies

### Architecture Highlights
- **Event Loop** - Custom event-driven loop for efficient I/O multiplexing
- **Modular Design** - Clean separation between configuration, parsing, and connection handling
- **Signal Handling** - Graceful shutdown with proper resource cleanup
- **Error Management** - Comprehensive error handling with custom exception classes

---

## 🛠️ Technical Stack

| Category | Technology |
|----------|------------|
| Language | C++98 |
| Build System | Makefile |
| I/O Model | Non-blocking with `poll()` |
| Platform | Linux / Unix |

---

## 📁 Project Structure

```
42_webserv/
├── Makefile                 # Build configuration
├── LICENSE                  # GPL v3 License
├── srcs/
│   ├── main. cpp            # Entry point
│   ├── EventLoop.*         # Event-driven I/O loop
│   ├── ConfigLoader.*      # Configuration file parser
│   ├── ServerConfig.*      # Server configuration management
│   ├── LocationConfig.*    # Location block configuration
│   ├── Listener.*          # Socket listener for incoming connections
│   ├── ListenerRegistry.*  # Manages multiple listeners
│   ├── Connection.*        # Client connection handling
│   ├── ConnectionManager. * # Connection pool management
│   ├── HttpRequest.*       # HTTP request representation
│   ├── HttpRequestParser.* # HTTP request parsing
│   ├── Response.*          # HTTP response builder
│   ├── CgiHandler.*        # CGI script execution
│   ├── CodePage.*          # HTTP status codes & error pages
│   ├── SignalHandler.*     # Unix signal handling
│   └── ... 
└── assets/
    └── server_cfgs/        # Example configuration files
```

---

## 🚀 Getting Started

### Prerequisites
- **GCC** or **Clang** compiler with C++98 support
- **Make** build tool
- Linux/Unix operating system

### Building

```bash
# Clone the repository
git clone https://github.com/PyrrhaSchnee/42_webserv. git
cd 42_webserv

# Build the project
make

# Build with debug symbols (optional)
make debug
```

### Running

```bash
# Run with default configuration
./webserv

# Run with custom configuration file
./webserv path/to/config. cfg
```

---

## ⚙️ Configuration Example

```nginx
server {
    listen 8080;
    server_name localhost;
    
    client_max_body_size 10M;
    
    error_page 404 /errors/404.html;
    error_page 500 /errors/500.html;
    
    location / {
        root /var/www/html;
        index index.html;
        allowed_methods GET;
    }
    
    location /upload {
        root /var/www/uploads;
        allowed_methods GET POST DELETE;
        upload_enable on;
    }
    
    location /cgi-bin {
        root /var/www/cgi;
        cgi . php /usr/bin/php-cgi;
        cgi . py /usr/bin/python3;
    }
}
```

---

## 🧪 Testing

You can test the server using tools like `curl`, `siege`, or your web browser:

```bash
# Simple GET request
curl http://localhost:8080/

# POST request with data
curl -X POST -d "data=test" http://localhost:8080/api

# File upload
curl -F "file=@image.png" http://localhost:8080/upload

# Test with multiple concurrent connections
siege -c 100 -t 30s http://localhost:8080/
```

---

## 📚 Skills Demonstrated

- **Network Programming**:  Socket programming, TCP/IP, HTTP protocol
- **Systems Programming**: Non-blocking I/O, event-driven architecture, signal handling
- **C++ Proficiency**: OOP principles, memory management, STL containers
- **Software Architecture**:  Modular design, separation of concerns
- **Problem Solving**: Implementing a complex specification from scratch
- **Code Quality**: Following strict coding standards (42 Norm)

---

## 👥 Authors

- **yang** - [@PyrrhaSchnee](https://github.com/PyrrhaSchnee)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [nginx](https://nginx.org/) for inspiration on configuration syntax

---

<p align="center">
  <i>Developed as part of the 42 School curriculum</i>
</p>
