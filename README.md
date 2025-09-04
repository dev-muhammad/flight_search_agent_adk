# Flight Search Agent using Google ADK

This project demonstrates how to create basic AI agent using Google's Agent Development Kit (ADK) that can help users find direct flights between cities. The agent uses Google Search to find flight information and provides intelligent responses to user queries.

## Features

- **Direct Flight Search**: Find direct flights between any two cities
- **Flight Information**: Get details about airlines, schedules, and pricing
- **Alternative Suggestions**: Receive suggestions for connecting flights when direct flights aren't available
- **Smart Query Processing**: Natural language understanding for flight requests

## Prerequisites

Before you begin, make sure you have:

1. **Python 3.8+** installed on your system
2. **Google AI Studio API Key** - Get one from [Google AI Studio](https://aistudio.google.com/apikey)
3. **Basic knowledge** of Python and command line operations

## Installation

### Step 1: Clone or Download the Project

```bash
git clone https://github.com/dev-muhammad/flight_search_agent_adk.git
cd flight_search_agent_adk
```

### Step 2: Create a Virtual Environment (Recommended)

```bash
# Create virtual environment
python -m venv flight_agent_env

# Activate virtual environment
# On macOS/Linux:
source flight_agent_env/bin/activate

# On Windows:
flight_agent_env\Scripts\activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Set Up Environment Variables

Copy the example environment file and configure your API key:

```bash
cp .env.example .env
```

Get your Google AI API key from [Google AI Studio](https://aistudio.google.com/apikey) and update the `.env` file:

```bash
GOOGLE_API_KEY=your_actual_api_key_here
```

## Usage

### Basic Usage

1. **Start the Agent with builtin WebUI**:

   ```bash
   adk web
   ```

2. **Interact with the Agent**:
   Once running, open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser. You can ask questions like:
   - "Find direct flights from New York to London"
   - "Are there any direct flights between Tokyo and Paris?"
   - "Show me flight options from Los Angeles to Dubai"
   - "What airlines fly direct from Mumbai to Singapore?"

### Production Deployment

**Important**: The built-in web UI is designed for development and testing purposes only.

For production deployment, you have several options:

- **Integration with existing applications**: Embed the agent into your web app or mobile app
- **API endpoints**: Deploy as a REST API service
- **Chat platforms**: Connect to Slack, Discord, or other messaging platforms
- **Cloud deployment**: Deploy on Google Cloud, AWS, or Azure

For detailed production deployment guides and examples, visit the [ADK Deployment Documentation](https://google.github.io/adk-docs/deploy/).

## Project Structure

```
flight_search_agent/
├── README.md                  # This file
├── requirements.txt           # Python dependencies
├── .env                       # Environment variables (create this)
├── .env.example               # Example of .env file
├── .gitignore                 # Git ignore file
└── flight_search_agent/       # Main agent directory
    ├── __init__.py            # Python package file
    └── agent.py               # Main agent implementation
```

## How It Works

### Agent Architecture

The flight search agent is built using Google's ADK and consists of:

1. **Agent Definition**: Defined in `flight_search_agent/agent.py`
2. **Google Search Tool**: Built-in ADK tool for web searches
3. **Instructions**: Detailed system prompt that guides the agent's behavior
4. **Model**: Uses Google's Gemini 2.0 Flash model for natural language processing

### Key Components

```python
from google.adk.agents import Agent
from google.adk.tools import google_search

root_agent = Agent(
    name="flight_search_agent",
    model="gemini-2.0-flash",
    description="Flight search agent for finding direct flights between cities",
    instruction="...",  # Detailed instructions for flight search behavior
    tools=[google_search],
)
```

## Customization

### Modifying Instructions

You can customize the agent's behavior by editing the `instruction` field in `agent.py`. For example:

- Add specific airline preferences
- Include price comparison features
- Add travel date flexibility options
- Include hotel and car rental suggestions

### Adding More Tools

You can extend the agent with additional tools:

```python
from google.adk.tools import google_search

def get_weather(city: str, unit: str):
    """
    Retrieves the weather for a city in the specified unit.

    Args:
        city (str): The city name.
        unit (str): The temperature unit, either 'Celsius' or 'Fahrenheit'.
    """
    # ... function logic ...
    return {"status": "success", "report": f"Weather for {city} is sunny."}

root_agent = Agent(
    # ... other parameters
    tools=[google_search, get_weather],
)
```

## Troubleshooting

### Common Issues

1. **API Key Not Working**:
   - Verify your API key is correct in the `.env` file
   - Ensure the key has proper permissions
   - Check if you've exceeded API rate limits

2. **Import Errors**:
   - Make sure you've installed all requirements: `pip install -r requirements.txt`
   - Verify you're using the correct Python version (3.8+)

3. **Agent Not Responding**:
   - Check your internet connection
   - Verify the Google ADK service is running
   - Look for error messages in the console

### Getting Help

If you encounter issues:

1. Check the [Google ADK documentation](https://google.github.io/adk-docs/)
2. Review the console output for error messages
3. Ensure all dependencies are properly installed

## Next Steps

Once you have the basic agent working, consider these enhancements:

1. **Add More Specific Search Queries**: Improve search precision for better results
2. **Price Comparison**: Integrate with flight booking APIs for real-time pricing
3. **Date Flexibility**: Add features to suggest alternative travel dates
4. **Multi-City Search**: Extend to handle complex itineraries
5. **User Preferences**: Store user preferences for personalized results

## Contributing

Feel free to contribute improvements to this project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Note: This project uses Google ADK, which has its own licensing terms. Please review Google ADK's license terms for commercial usage.

## Related Resources

- [Google ADK Documentation](https://github.com/google/adk)
- [Google AI Studio](https://aistudio.google.com)
- Article: 
    - [Как создавать ИИ-агентов: практическое руководство для новых разработчиков](https://the-tech.kz/kak-sozdavat-ii-agentov-prakticheskoe-rukovodstvo-dlya-novyh-razrabotchikov/)

---

**Note**: This project was created as a demonstration for the article "How to Create AI Agents: A Practical Guide for New Developers"
