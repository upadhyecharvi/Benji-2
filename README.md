from gtts import gTTS
import vlc
import time

text_to_speech = gTTS(text="hello world!")
text_to_speech.save('sample.mp3')
player=vlc.MediaPlayer('C:\pdtp\sample.mp3')
player.play()
time.sleep(10)

import speech_recognition as sr
import pyaudio

r = sr.Recognizer()
with sr.Microphone() as source:
    print("Speak:")
    audio = r.listen(source)

try:
    print("You said " + r.recognize_google(audio))
except sr.UnknownValueError:
    print("Could not understand audio")
except sr.RequestError as e:
    print("Could not request results; {0}".format(e))
