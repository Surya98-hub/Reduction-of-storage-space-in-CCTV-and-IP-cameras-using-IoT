# Reduction-of-storage-space-in-CCTV-and-IP-cameras-using-IoT

from picamera import PiCamera
import RPi.GPIO as GPIO
import time
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)
#Read output from PIR motion sensor
GPIO.setup(11, GPIO.IN)
#LED output pin 
GPIO.setup(3, GPIO.OUT) 
while True:
i=GPIO.input(11)
#When output from motion sensor is LOW
if i==0: 
print "No intruders",i
camera.stop_recording()
for f in camera.capture_continuous(rawCapture, format="bgr", 
use_video_port=True):
# grab the raw NumPy array representing the image and initialize
# the timestamp and occupied/unoccupied text
frame = f.array
timestamp = datetime.datetime.now()
# resize the frame, convert it to grayscale, and blur it
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
gray = cv2.GaussianBlur(gray, tuple(conf['blur_size']), 0)
if avg is None:
print "[INFO] starting background model..."
# accumulate the weighted average between the current frame and
# previous frames, then compute the difference between the current
# frame and running average
frameDelta = cv2.absdiff(gray, cv2.convertScaleAbs(avg))
cv2.accumulateWeighted(gray, avg, 0.5)
avg = gray.copy().astype("float")
rawCapture.truncate(0)
#Turn OFF LED
GPIO.output(3, 0) 
time.sleep(0.1)
#When output from motion sensor is HIGH
elif i==1: 
print "Intruder detected",i
camera.start_recording('/home/pi/Desktop/video.h264')
#Turn ON LED
GPIO.output(3, 1) 
time.sleep(0.1)
else:
camera.start_preview()
