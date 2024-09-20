# Negotiation_Chatbot

Here’s a suggested structure and content for the README file in your GitHub repository:

Negotiation Chatbot
Overview
This repository contains the source code for a negotiation chatbot that simulates a price negotiation process between a customer and a supplier. The chatbot leverages a pre-trained AI model from Google Gemini to handle the conversational aspect of the negotiation. The chatbot aims to maximize the sale price with minimal discounts, while allowing the user to propose counteroffers or accept/reject the offer.

Features
Product Negotiation: The chatbot negotiates the price of a product (e.g., a laptop) with the customer, offering small concessions based on the customer’s counteroffers.
Pricing Logic: Implements logic to handle discounts within a specified range and ensure prices decrease with each negotiation round.
AI Model Integration: Uses the Google Gemini pre-trained language model to generate persuasive, concise negotiation responses.
Politeness Bonus (Optional): Sentiment analysis can be incorporated to improve outcomes, offering better deals if the customer is polite.
How It Works
The chatbot is initialized with a product, base price, and a discount range. During the negotiation, the chatbot engages the user by presenting the current price and responding to the user's offers or decisions (accept/reject). The AI model generates responses that are focused on securing the deal with minimal discounts.

Conversation Flow
Initiate Negotiation: The chatbot starts by presenting the base price of the product.
User Input: The user can either propose a new price, accept the current price, or reject the offer.
AI Response: The chatbot uses the Gemini model to generate a response, either accepting the offer, rejecting it, or proposing a counteroffer.
Loop or End: The conversation continues until the user accepts, rejects, or the negotiation reaches the maximum number of rounds.
Integration with Google Gemini Model
The chatbot is powered by the Google Gemini generative AI model, which handles the conversational logic. Here’s a step-by-step guide on how the integration is achieved:

API Configuration:

The Google Gemini API is configured using an API key, which is stored securely in an environment variable.
python
Copy code
import google.generativeai as genai
genai.configure(api_key="Your_API_Key_Here")
Model Initialization:

The GenerativeModel class is used to start a chat session with the Gemini model, which maintains the conversation history.
python
Copy code
self.model = genai.GenerativeModel('gemini-pro')
self.chat = self.model.start_chat(history=[])
Generating AI Responses:

Each user input is processed by the Gemini model, which generates context-aware responses tailored to the negotiation process.
python
Copy code
response = self.chat.send_message(f"{system_prompt}\n\nUser: {user_message}")
return response.text
Customizing AI Prompts:

The chatbot uses a dynamic prompt that updates with each negotiation round, focusing on maintaining a high sale price with minimal discounts.
python
Copy code
system_prompt = f"""
You are a salesperson negotiating the price of a {self.product.name}.
Current price: ${self.current_price}
Base price: ${self.product.base_price}
Negotiation round: {self.negotiation_rounds + 1} of {self.max_rounds}

Respond as a determined salesperson focused on securing a deal with minimal discount from the base price. 
Emphasize the product's value and fairness of the base price, and make only small concessions. 
Encourage the customer to close the deal soon.
Keep coversation short and concise.
Address the customer directly, using "you" instead of "the customer."
"""
Usage
To use this chatbot, follow these steps:

Clone the Repository:

bash
Copy code
git clone https://github.com/Stephenca290/Negotiation_Chatbot.git
cd Negotiation_Chatbot
Set Up the Environment:

Ensure Python is installed on your system.
Install required libraries, primarily the Google Generative AI library.
bash
Copy code
pip install google-generative-ai
Run the Chatbot:

Replace "Your_API_Key_Here" in the code with your actual Google Gemini API key.
Execute the script to start the negotiation chatbot.
bash
Copy code
python chatbot.py
Interact with the Chatbot:

Follow the on-screen instructions to negotiate the price of the product.
Demo
A demo video showcasing the negotiation process can be found here.

Contributing
Contributions are welcome! If you have suggestions or find issues, feel free to open an issue or submit a pull request.

License
This project is licensed under the MIT License - see the LICENSE file for details.
