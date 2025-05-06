# Alarm-Clock
import datetime
import time
import winsound  # For Windows sound alert

def set_alarm():
    alarm_time = input("Set the alarm time (HH:MM:SS, 24-hour format): ")
    
    try:
        alarm_hour, alarm_minute, alarm_second = map(int, alarm_time.split(":"))
    except ValueError:
        print("Invalid time format. Please use HH:MM:SS format.")
        return

    print(f"Alarm set for {alarm_time}...")

    while True:
        now = datetime.datetime.now()
        current_time = now.strftime("%H:%M:%S")

        if current_time == alarm_time:
            print("⏰ Wake up! Alarm time reached!")
            try:
                # Windows sound alert
                for i in range(5):
                    winsound.Beep(1000, 1000)  # frequency, duration
            except:
                print("Alarm sound failed.")
            break
        
        time.sleep(1)

if __name__ == "__main__":
    set_alarm()
