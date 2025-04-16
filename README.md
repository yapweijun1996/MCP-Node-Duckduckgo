# MCP Node DuckDuckGo Server

A Node.js application serving as an MCP server that offers two main tools:
- **Search**: Query DuckDuckGo and retrieve formatted search results.
- **Fetch Content**: Retrieve and parse text content from any webpage URL.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Starting the Server](#starting-the-server)
  - [Available Endpoints](#available-endpoints)
    - [List Tools](#list-tools)
    - [Search Tool](#search-tool)
    - [Fetch Content Tool](#fetch-content-tool)
- [Logging and Debugging](#logging-and-debugging)
- [Contributing](#contributing)
- [License](#license)

## Overview

The MCP Node DuckDuckGo Server is a Node.js server that provides a modular interface (via HTTP endpoints) to query DuckDuckGo and fetch webpage content. This project showcases:
- Express for server creation.
- Axios for making HTTP requests.
- Cheerio for parsing HTML.

## Features

- **DuckDuckGo Search**: Uses a POST API to execute search queries and return DuckDuckGo results formatted for further processing.
- **Web Content Fetching**: Retrieves and parses text content from a given URL.
- **Rate Limiting**: Provides basic rate limiting to manage the request frequency.
- **Extensible MCP Server**: Tools are organized as modules, making it easy to add or modify functionality.

## Requirements

- Node.js (v12 or higher)
- npm

## Installation

1. **Clone the Repository**  
   Clone the repository from GitHub:
   ```bash
   git clone <repository-url>
   ```

2. **Navigate to the Project Folder**  
   ```bash
   cd mcp-node-duckduckgo-server
   ```

3. **Install Dependencies**  
   Install required packages using npm:
   ```bash
   npm install express axios cheerio
   ```

## Usage

### Starting the Server

Run the server by executing:
```bash
node mcp-node-duckduckgo-server.js
```
You should see a log message similar to:
```
MCP Server "ddg-search" running on port 3000
```

### Available Endpoints

#### List Tools

To list all available tools, open a new terminal window and run:
```bash
curl http://localhost:3000/tools
```
This should output a JSON list of registered tools (e.g., "search" and "fetchContent").

#### Search Tool

Execute a search query using the search tool:
```bash
curl -X POST http://localhost:3000/run-tool \
-H "Content-Type: application/json" \
-d '{"toolName": "search", "params": {"query": "test query", "maxResults": 5}}'
```
The response will contain the formatted search results from DuckDuckGo.

#### Fetch Content Tool

Fetch content from a specific webpage:
```bash
curl -X POST http://localhost:3000/run-tool \
-H "Content-Type: application/json" \
-d '{"toolName": "fetchContent", "params": {"url": "https://example.com"}}'
```
The server will return a text snippet from the fetched webpage.

## Logging and Debugging

- The server logs informational and error messages to the terminal.
- Use these logs to debug issues such as timeouts, HTTP errors, or unexpected behavior in responses.

## Contributing

Contributions are welcome! If you want to contribute:
1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/YourFeature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
