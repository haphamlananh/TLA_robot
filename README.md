# TLA_robot
trợ lý ảo đơn gian bằng tiếng anh
import  speech_recognition 
import pyttsx3
from datetime import date, datetime
import wikipedia
import pyowm
from pyowm import owm

robot_ear = speech_recognition.Recognizer()
robot_mouth = pyttsx3.init()
robot_brain = ""
while True:
	with speech_recognition.Microphone() as mic: #lấy mic của pc này
		print("robot: Tôi đang nghe, bạn hãy nói gì đó")
		audio = robot_ear.listen(mic, timeout=3, phrase_time_limit=3)
	try:
		you = robot_ear.recognize_google(audio, language = "vi-VN") 
	except:
		you = ""
	print("you: " + you) 

	if you == "":
		robot_brain = "i can't hear you, try again"
	elif "hello" in you:
		robot_brain =" hello ha pham lan anh"
	elif "today" in you:
		today = date.today()
		robot_brain = today.strftime("%B %d, %Y")
	elif "time" in you:
		now = datetime.today()
		robot_brain = now.strftime("%H hours %M minutes %S seconds")
	elif "President 45" in you:
		print(wikipedia.summary("donald trump", sentences = 1))
		robot_mouth.say(wikipedia.summary("donald trump", sentences = 1))	
		robot_mouth.runAndWait()
	elif "u s a " in you:
		print(wikipedia.summary("U.S. president", sentences = 1))
		robot_mouth.say(wikipedia.summary("U.S. president", sentences = 1))	
		robot_mouth.runAndWait()
	elif "singer" in you:
		print(wikipedia.summary("son tung mtp", sentences = 1))
		robot_mouth.say(wikipedia.summary("son tung mtp", sentences = 1))	
		robot_mouth.runAndWait()
	elif "vietnam" in you:
		print(wikipedia.summary("vietnam", sentences = 1))
		robot_mouth.say(wikipedia.summary("vietnam", sentences = 1))	
		robot_mouth.runAndWait()
	elif "sing" in you:
		print(wikipedia.summary("son tung mtp", sentences = 1))
		robot_mouth.say(wikipedia.summary("son tung mtp", sentences = 1))	
		robot_mouth.runAndWait()
	elif "bye" in you:
		robot_brain = " bye ha pham lan anh"
		print("robot:" + robot_brain)
		robot_mouth.say(robot_brain)
		robot_mouth.runAndWait()
		break
	else :
		robot_brain = "thank you"

	print("robot:" + robot_brain)
	robot_mouth.say(robot_brain)
	robot_mouth.runAndWait()
