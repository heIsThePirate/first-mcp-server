# Wikipedia MCP Server

A Model Context Protocol (MCP) server that provides Wikipedia search and content retrieval capabilities. This server allows AI assistants and other MCP clients to search Wikipedia, retrieve article summaries, list article sections, and get specific section content.

## Features

This MCP server exposes the following tools:

### 1. `fetch_wikipedia_info`
Search Wikipedia for a topic and return the title, summary, and URL of the best match.

**Parameters:**
- `query` (string): The search term or topic to look up

**Returns:**
- `title`: The title of the Wikipedia article
- `summary`: A brief summary of the article
- `url`: The URL to the Wikipedia page
- `error`: Error message if the search fails or is ambiguous

### 2. `list_wikipedia_sections`
Get a list of all section titles from a Wikipedia article.

**Parameters:**
- `topic` (string): The Wikipedia article title

**Returns:**
- `sections`: Array of section titles from the article
- `error`: Error message if the article cannot be found

### 3. `get_section_content`
Retrieve the content of a specific section from a Wikipedia article.

**Parameters:**
- `topic` (string): The Wikipedia article title
- `section_title` (string): The specific section to retrieve

**Returns:**
- `content`: The text content of the specified section
- `error`: Error message if the article or section cannot be found

## Installation

1. Clone this repository:
```bash
git clone https://github.com/heIsThePirate/first-mcp-server.git
cd first-mcp-server
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

## Usage

Run the MCP server:
```bash
python mcp_server.py
```

The server will start and listen for MCP protocol messages via stdio transport.

## Requirements

- Python 3.7+
- wikipedia==1.4.0
- mcp>=1.0.0

## Error Handling

The server handles common Wikipedia API errors:
- **DisambiguationError**: When a search term matches multiple articles, returns suggestions
- **PageError**: When a page cannot be loaded
- **General exceptions**: Gracefully handled with descriptive error messages

## Example Use Cases

- Research assistance by searching and summarizing Wikipedia articles
- Content exploration by browsing article sections
- Educational tools that need access to encyclopedic information
- AI assistants that need to provide factual information from Wikipedia

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is open source and available under the MIT License.
