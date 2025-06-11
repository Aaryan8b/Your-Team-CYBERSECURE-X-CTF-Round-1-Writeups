# SASSYGPT_HARDCORE

this python script acts as middile man to talk with ai
and this ag gave the flag with just hre keyword hello
```python
import requests
def chat_with_sassygpt():
    url = "https://cybersecure-x-sassygpt-hardcore.chals.io/ask"
    headers = {
        "Content-Type": "application/json"
    }

    print("Welcome to SassyGPT Chat! (Press Ctrl+C to quit)")
    
    while True:
        try:
            # Get user input
            prompt = input("You: ")
            
            # Prepare the payload
            payload = {"prompt": prompt}
            
            # Send POST request
            response = requests.post(url, json=payload, headers=headers)
            
            # Check if the request was successful
            if response.status_code == 200:
                data = response.json()
                print("SassyGPT:", data.get("response", "No response found"))
            else:
                print(f"Error: HTTP {response.status_code} - {response.text}")
                
        except KeyboardInterrupt:
            print("\nGoodbye!")
            break
        except Exception as e:
            print(f"An error occurred: {e}")

if __name__ == "__main__":
    chat_with_sassygpt()
```
![image](https://github.com/user-attachments/assets/a413382a-3a17-4753-b8dd-471aef39f75b)

# FLAG
```
flag{prompt_pathway_mastered}
```
