pip install speechrecognition pyttsx3 pyaudio
import speech_recognition as sr
import pyttsx3

# Initialize Text-to-Speech (TTS) engine
engine = pyttsx3.init()
engine.setProperty("rate", 150)  # Speed of speech
engine.setProperty("volume", 1)  # Volume (0.0 to 1.0)

def speak(text):
    """Convert text to speech"""
    engine.say(text)
    engine.runAndWait()

def listen():
    """Recognize speech from the microphone"""
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        recognizer.adjust_for_ambient_noise(source)  # Adjust for background noise
        try:
            audio = recognizer.listen(source)
            command = recognizer.recognize_google(audio)
            print(f"You said: {command}")
            return command.lower()
        except sr.UnknownValueError:
            speak("Sorry, I didn't understand that.")
            return None
        except sr.RequestError:
            speak("Network error. Please try again.")
            return None

# Main loop
if __name__ == "__main__":
    speak("Hello! How can I assist you?")
    while True:
        command = listen()
        if command:
            if "exit" in command:
                speak("Goodbye!")
                break
            elif "hello" in command:
                speak("Hi there!")
            else:
                speak(f"You said: {command}")
