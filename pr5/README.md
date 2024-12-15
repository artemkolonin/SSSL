Создаём сеть с Wazuh, как в пр3

![image](https://github.com/user-attachments/assets/5410b458-c988-495a-9ca3-2e9587a7da2f)

Устанавливаем suricata

![image](https://github.com/user-attachments/assets/5b4a9003-d120-453c-87a2-2e7a3cb3e24f)

Включаем просмотр логов от suricata

![image](https://github.com/user-attachments/assets/d01fbde8-d2d2-4160-a561-84b07df1196e)

Видим логи с suricata

![image](https://github.com/user-attachments/assets/582f1ecb-3e02-4f6a-a3ad-71ccb0fbde9f)

Поднимаем apache для проверки suricata

![image](https://github.com/user-attachments/assets/f5f4411e-6812-4c8c-b1d7-8bf217ca3b06)

Настраиваем suricata на нужный интерфейс

![image](https://github.com/user-attachments/assets/7a9f437a-d41a-42aa-a63a-d9b4197844e9)

Устанавливаем и используем Nikto для сканирования apache

![image](https://github.com/user-attachments/assets/bb7a592c-36c2-497b-88e7-f7f33cbedf1f)

![image](https://github.com/user-attachments/assets/ca682b59-f96f-47aa-b83c-e110e0928ad7)

Лог suricata

![image](https://github.com/user-attachments/assets/bc0e9520-4c90-4f30-92c3-e542ae1a907f)

Устанавливаем yara

![image](https://github.com/user-attachments/assets/660377ec-7bba-4cf6-a03b-a03dc7a5ea19)

Создаём правило

![image](https://github.com/user-attachments/assets/24f8bc39-c025-43ad-a078-a75e9eb3ca25)

Триггерим правило

![image](https://github.com/user-attachments/assets/30674bbf-6762-4c56-bc8e-d792885290f3)

Лог в wazuh с yara

![image](https://github.com/user-attachments/assets/e6c99b7d-b637-406a-b04e-28d589736ae2)
