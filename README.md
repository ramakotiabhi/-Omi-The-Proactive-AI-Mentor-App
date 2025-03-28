This file should provide an overview of the project, setup instructions, and usage examples.

# Omi: The Proactive AI Mentor App

Omi is an AI wearable that records your conversations and provides personalized advice via in-app notifications. This project aims to create the most helpful AI mentor that assists you throughout your day.

## Features

- **Chat Prompts:** Customize Omi’s conversational style.
- **Memory Prompts:** Summarize conversations and extract key points.
- **Integration Apps:** Connect to external services for enhanced functionality.
- **Real-Time Transcript Processing:** Get live advice and feedback.

## Constants
ANALYSIS_INTERVAL = 5 # seconds between analyses
REMINDER_INTERVAL = 10 # seconds after last notification before sending reminder
REMINDER_CHECK_INTERVAL = 2 # check interval for reminders

logger = logging.getLogger(name)
logger.setLevel(logging.DEBUG)

## Set up logging handler (for demo purposes, outputting to console)
handler = logging.StreamHandler()
formatter = logging.Formatter('%(asctime)s - %(levelname)s - [%(threadName)s] - %(module)s:%(lineno)d - %(message)s')
handler.setFormatter(formatter)
logger.addHandler(handler)

## Initialize OpenAI client
try:
client = OpenAI(api_key=os.getenv('OPENAI_API_KEY'))
if not os.getenv('OPENAI_API_KEY'):
logger.error("OPENAI_API_KEY not found in environment variables")
raise ValueError("OPENAI_API_KEY environment variable is required")
logger.info("OpenAI client initialized successfully")
except Exception as e:
logger.critical(f"Failed to initialize OpenAI client: {str(e)}", exc_info=True)
raise

app_routes = Blueprint('app_routes', name)   
## Data Formats

Conversations
Each entry in conversations.json includes:

session_id: Unique identifier for each session.
messages: List of message objects with timestamp, speaker, and text.
mentor_response: Example response generated after analyzing the conversation.

## Contributing

Feel free to fork the repository, submit issues, or provide pull requests. Contributions are welcome!   

## *WARNING*

Remember to replace placeholder API keys and URLs with your actual values. This detailed structure and example data will help you create a well-organized and informative GitHub repository. You can then expand upon this foundation by adding more sophisticated features and data as your project evolves.

This design focuses on proactive guidance, personalized feedback, and seamless integration with the user's digital life, making Omi a truly helpful and indispensable AI mentor.

