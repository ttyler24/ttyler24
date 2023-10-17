import openai

Authorization: Bearer OPENAI_API_KEY
openai.api_key = 'YOUR_OPENAI_API_KEY'

def chat_with_ai(prompt):
    response = openai.Completion.create(
        engine="text-davinci-003",
        prompt=prompt,
        max_tokens=150,  # Adjust the response length as needed
        n=1,
        stop=None
    )
    return response.choices[0].text.strip()

print("Hello! You can start chatting with me. Type 'exit' to end the conversation.")
while True:
    user_input = input("You: ")
    if user_input.lower() == 'exit':
        print("Goodbye!")
        break
    prompt = f"You: {user_input}\nChatGPT:"
    ai_response = chat_with_ai(prompt)
    print(f"ChatGPT: {ai_response}")
