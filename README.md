# Mercor-Healthcare-Chatbot

This Python code defines a GuardedChatbot class that uses the OpenAI API to respond to user input while also being cautious about harmful or sensitive content. Let's go through the code step by step:

1. Importing necessary libraries and modules:
* **openai**: This module allows interaction with the OpenAI GPT-3 language model.
* **re**: This module is used for regular expression pattern matching.

2.Setting up the API Key:
Replace **'YOUR_OPENAI_API_KEY'** with your actual OpenAI API key, allowing access to the GPT-3 API.

3.Defining the **''GuardedChatbot''** class:
The class encapsulates the chatbot's behavior and capabilities.

4.Defining the harmful and emergency patterns:
-->The class defines two lists: **'HARMFUL_PATTERNS'** and **'EMERGENCY_PATTERNS'**.
-->**'HARMFUL_PATTERNS'** contains regular expression patterns that may be considered harmful or sensitive.
-->**'EMERGENCY_PATTERNS'** contains regular expression patterns that indicate an emergency situation.

5.Initializing the chatbot:
-->The constructor **'__init__(self)'** sets up initial states for the chatbot.
-->**'self.context_history'** is a list that will store the user's input history for contextual responses.
-->**'self.in_sensitive_mode'** is a flag that indicates if the chatbot is currently in sensitive mode due to harmful content.

6.Helper methods:
-->**'contains_harmful_pattern(self, text)'**: This method checks if the given **'text'** contains any harmful patterns from the **'HARMFUL_PATTERNS'** list.
-->**'contains_emergency_pattern(self, text)'**: This method checks if the given **'text'** contains any emergency patterns from the **'EMERGENCY_PATTERNS'** list.

7.**'get_response(self, prompt)'** method:
-->This method takes a **'prompt'** as input, which is the user's message.
-->If the **'prompt'** contains an emergency pattern, the method returns a predefined emergency response, urging the user to seek immediate assistance.
-->If the **'prompt'** contains harmful content or if the chatbot is in sensitive mode, the chatbot asks how it can comfort someone based on the user's message and updates the prompt accordingly.
-->The method then uses the OpenAI API to generate a response based on the modified **'prompt'**.
-->The generated **'chatbot_response'** is checked for harmful or emergency patterns. If found, a specific message is returned.
-->Otherwise, the **'chatbot_response'** is returned as the final response.

8.**'fallback_response(self)'** method:
This method provides a generic response to the user when no appropriate response can be generated.

9.**'chat(self)'** method:
-->This method initiates a chat session with the user.
-->It prints a welcome message and a reminder that the chatbot is not a replacement for professional help.
-->It then enters a loop to receive user input.
-->If the user enters "exit," the chat loop terminates.
-->For each user input, the **'get_response'** method is called to generate the chatbot's response.
-->If the chatbot's response is the same as the last context in the history (to avoid repetitive responses), the fallback response is provided.
-->The chatbot's response is printed to the console.

10.Running the chatbot:
If the script is executed as the main module (**'if __name__ == '__main__':'**), a 'GuardedChatbot' instance is created, and the **'chat'** method is called to start the chat session.

Overall, this code creates a chatbot that can interact with users using the GPT-3 model, but it is designed with safety in mind by being cautious about harmful or emergency content. If harmful patterns are detected in user input, the chatbot tries to offer comfort and avoid generating harmful responses. For emergency situations, the chatbot advises the user to seek immediate professional help.

