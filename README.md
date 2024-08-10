- 👋 Hi, I’m @Shri-hub-c
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Shri-hub-c/Shri-hub-c is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->python -m venv voice_calculator_env
source voice_calculator_env/bin/activate  # On Windows, use `voice_calculator_env\Scripts\activate`
pip install speech_recognition pyttsx3 pyaudio
import speech_recognition as sr
import pyttsx3

# Initialize the recognizer and the text-to-speech engine
recognizer = sr.Recognizer()
engine = pyttsx3.init()

def speak(text):
    engine.say(text)
    engine.runAndWait()

def listen():
    with sr.Microphone() as source:
        print("Listening...")
        audio = recognizer.listen(source)
        try:
            text = recognizer.recognize_google(audio)
            print(f"You said: {text}")
            return text
        except sr.UnknownValueError:
            speak("Sorry, I did not understand that.")
            return None
        except sr.RequestError:
            speak("Sorry, there was an error with the speech recognition service.")
            return None

def calculate(expression):
    try:
        # Evaluate the mathematical expression
        result = eval(expression)
        return result
    except Exception as e:
        speak("There was an error with the calculation.")
        return None

def main():
    speak("Say a mathematical expression to calculate.")
    expression = listen()
    if expression:
        result = calculate(expression)
        if result is not None:
            speak(f"The result is {result}")
            print(f"The result is {result}")
        else:
            speak("Could not calculate the result.")
    else:
        speak("No expression was received.")

if __name__ == "__main__":
    main()
python voice_calculator.py
pip install pyinstaller
pyinstaller --onefile voice_calculator.py
git clone https://github.com/your_username/voice_calculator.git
git add .
git commit -m "Initial commit"
git push origin main

