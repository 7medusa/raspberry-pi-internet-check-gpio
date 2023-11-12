import RPi.GPIO as GPIO
import subprocess
import platform
import time

GPIO.setmode(GPIO.BCM)
led_pin = 26 #you can change this
GPIO.setup(led_pin, GPIO.OUT)


def led_on():
    GPIO.output(led_pin, GPIO.HIGH)
    print("LED eingeschaltet")


def led_off():
    GPIO.output(led_pin, GPIO.LOW)
    print("LED ausgeschaltet")


def blinken():
    time.sleep(0.2)
    led_on()
    time.sleep(0.2)
    led_off()


def internet():
    command = "ping -c 1 google.com" if platform.system().lower() == "linux" else None

    if command:
        try:
            subprocess.check_output(command, shell=True)
            return True
        except subprocess.CalledProcessError:
            return False
    else:
        print("the programm is only for linux")


if __name__ == "__main__":
    try:
        while True:
            if internet():
                led_on()
            elif not internet():
                blinken()
            time.sleep(2)
    except KeyboardInterrupt:
        GPIO.cleanup()
        exit()
