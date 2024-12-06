import speech_recognition as sr
import pyttsx3
import datetime
import webbrowser
import os
import subprocess

# Initialize Text-to-Speech engine
engine = pyttsx3.init()
engine.setProperty('rate', 150)  # Speed of speech
engine.setProperty('volume', 1.0)  # Volume level

# Function to make Jarvis speak
def speak(text):
    engine.say(text)
    engine.runAndWait()

# Function to listen for user commands
def take_command():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        recognizer.pause_threshold = 1  # Adjust pause threshold for better accuracy
        try:
            audio = recognizer.listen(source, timeout=5)
            print("Recognizing...")
            command = recognizer.recognize_google(audio, language="en-in")
            print(f"User said: {command}\n")
        except Exception as e:
            print("Sorry, I didn't catch that. Please repeat.")
            return None
    return command.lower()

# Core function to execute commands
def execute_command(command):
    if "time" in command:
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        speak(f"The time is {current_time}")
    
    elif "date" in command:
        current_date = datetime.datetime.now().strftime("%Y-%m-%d")
        speak(f"Today's date is {current_date}")
    
    elif "open google" in command:
        speak("Opening Google")
        webbrowser.open("https://www.google.com")
    
    elif "play music" in command:
        music_dir = "C:\\Users\\YourUsername\\Music"  # Replace with your music directory
        songs = os.listdir(music_dir)
        if songs:
            os.startfile(os.path.join(music_dir, songs[0]))
            speak("Playing music")
        else:
            speak("No music files found in the directory.")
    
    elif "open notepad" in command:
        speak("Opening Notepad")
        subprocess.run("notepad.exe")
    
    elif "exit" in command or "quit" in command:
        speak("Goodbye!")
        exit()
    
    else:
        speak("I didn't understand the command. Please try again.")

# Main function
def jarvis():
    speak("Hello, I am Jarvis. How can I assist you today?")
    while True:
        command = take_command()
        if command:
            execute_command(command)

# Run Jarvis
if __name__ == "__main__":
    jarvis()
    
