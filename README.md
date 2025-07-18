# Wikipedia MCP Server

A comprehensive Model Context Protocol (MCP) server that provides Wikipedia search and content retrieval capabilities, along with an interactive client application. This server allows AI assistants and other MCP clients to search Wikipedia, retrieve article summaries, list article sections, get specific section content, and includes intelligent prompts and resources for enhanced Wikipedia exploration.

## Features

### MCP Server Tools

This MCP server exposes the following tools:

#### 1. `fetch_wikipedia_info`
Search Wikipedia for a topic and return the title, summary, and URL of the best match.

**Parameters:**
- `query` (string): The search term or topic to look up

**Returns:**
- `title`: The title of the Wikipedia article
- `summary`: A brief summary of the article
- `url`: The URL to the Wikipedia page
- `error`: Error message if the search fails or is ambiguous

#### 2. `list_wikipedia_sections`
Get a list of all section titles from a Wikipedia article.

**Parameters:**
- `topic` (string): The Wikipedia article title

**Returns:**
- `sections`: Array of section titles from the article
- `error`: Error message if the article cannot be found

#### 3. `get_section_content`
Retrieve the content of a specific section from a Wikipedia article.

**Parameters:**
- `topic` (string): The Wikipedia article title
- `section_title` (string): The specific section to retrieve

**Returns:**
- `content`: The text content of the specified section
- `error`: Error message if the article or section cannot be found

### MCP Server Prompts

#### `highlight_sections_prompt`
Identifies the most important sections from a Wikipedia article on a given topic.

**Parameters:**
- `topic` (string): The Wikipedia article topic

**Purpose:** Helps users focus on the most relevant and interesting sections of lengthy Wikipedia articles by providing intelligent recommendations with explanations.

### MCP Server Resources

#### `suggested_titles`
Provides a curated list of suggested Wikipedia topics for exploration.

**URI:** `file://suggested_titles`

**Returns:** List of suggested Wikipedia topics loaded from `suggested_titles.txt`

**Current Topics:**
- coronavirus
- python language
- prompt engineering
- node.js
- photosynthesis
- the solar system

## Interactive Client Application

The project includes a sophisticated interactive client (`mcp_client.py`) that demonstrates how to use the MCP server with AI capabilities:

### Client Features

- **LangGraph Integration**: Uses LangGraph for stateful conversation management
- **OpenAI GPT-4 Integration**: Powered by OpenAI's GPT-4 for intelligent responses
- **Interactive Commands**: Special commands for exploring MCP capabilities
- **Memory Management**: Maintains conversation context across interactions

### Client Commands

- `/prompts` - List all available prompts on the server
- `/prompt <name> "args"` - Execute a specific prompt with arguments
- `/resources` - List all available resources on the server
- `/resource <name>` - Access a specific resource
- Regular chat - Ask questions that will be answered using Wikipedia tools

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

3. Set up your OpenAI API key:
   - Copy the `.env` file and add your OpenAI API key
   - Or set the `OPENAI_API_KEY` environment variable

## Usage

### Running the MCP Server

Run the MCP server standalone:
```bash
python mcp_server.py
```

The server will start and listen for MCP protocol messages via stdio transport.

### Running the Interactive Client

Run the interactive client application:
```bash
python mcp_client.py
```

This will start an interactive session where you can:
- Ask questions about Wikipedia topics
- Use special commands to explore prompts and resources
- Have AI-powered conversations with Wikipedia integration

### Example Client Session

```
Wikipedia MCP agent is ready.
Type a question or use the following templates:
  /prompts                - to list available prompts
  /prompt <name> "args"   - to run a specific prompt
  /resources              - to list available resources
  /resource <name>        - to run a specific resource

You: Tell me about Python programming language
AI: [AI response with Wikipedia information about Python]

You: /resources
Available Resources:
[1] suggested_titles

You: /resource suggested_titles
=== Resource Text ===
coronavirus
python language
prompt engineering
node.js
photosynthesis
the solar system
```

## Requirements

### Core Dependencies
- Python 3.7+
- wikipedia==1.4.0
- mcp>=1.0.0

### Client Dependencies (for interactive client)
- langchain-openai
- langgraph
- langchain-mcp-adapters
- python-dotenv

## Configuration

The project uses environment variables for configuration:

- **OPENAI_API_KEY**: Your OpenAI API key (required for the interactive client)

Configuration is managed through:
- `.env` file for environment variables
- `config.py` for loading and managing configuration

## Error Handling

The server handles common Wikipedia API errors:
- **DisambiguationError**: When a search term matches multiple articles, returns suggestions
- **PageError**: When a page cannot be loaded
- **General exceptions**: Gracefully handled with descriptive error messages

## Project Structure

```
first-mcp-server/
├── mcp_server.py           # Main MCP server implementation
├── mcp_client.py           # Interactive client application
├── config.py               # Configuration management
├── .env                    # Environment variables
├── suggested_titles.txt    # Curated list of Wikipedia topics
├── requirements.txt        # Python dependencies
└── README.md              # This file
```

## Example Use Cases

- **Research assistance**: Search and summarize Wikipedia articles with AI-powered insights
- **Content exploration**: Browse article sections with intelligent recommendations
- **Educational tools**: Access encyclopedic information with guided exploration
- **AI assistants**: Provide factual information from Wikipedia with conversational interface
- **Interactive learning**: Explore topics through prompts and curated suggestions

## Contributing

Feel free to submit issues and enhancement requests! Areas for contribution:
- Additional Wikipedia tools and capabilities
- Enhanced prompts for better content discovery
- Expanded resource collections
- Client interface improvements

## License

This project is open source and available under the MIT License.
