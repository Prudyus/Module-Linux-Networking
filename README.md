# Module-Linux-Networking
EPAM University Programs DevOps external course Module – Linux Networking

Server_1 – Віртуальна машина, на якій розгорнуто ОС Linux. Int1 цієї машини в 
режимі «Мережевий міст» підключений до мережі Net1, тобто знаходиться в адресному 
просторі домашньої мережі. IP-адреса Int1 встановлюється статично відповідно до 
адресного простору. Інтерфейси Int2 та Int3 відповідно 
підключено в режимі «Внутрішня мережа» до мереж Net2 та Net3.
![Снимок экрана (448)](https://user-images.githubusercontent.com/102302310/215271673-9657b562-1299-4046-bfbf-94a6bae76c3d.png)
![enp0s3](https://user-images.githubusercontent.com/102302310/215272209-e53e4cfc-ce33-4cd6-a182-02297c26c903.jpg)
![net2](https://user-images.githubusercontent.com/102302310/215272217-d10596da-a290-4361-90ba-2c87e83c4f84.jpg)
![net3](https://user-images.githubusercontent.com/102302310/215272226-46f761ec-0b86-4425-a718-18384fd46771.jpg)

Client_1 – віртуальна машина, на якій розгорнуто ОС Linux  Ubuntu

Інтерфейси підключені в режимі «Внутрішня мережа» до мереж Net2 та Net4 як показано на малюнку
![изображение_viber_2023-01-28_16-38-46-151](https://user-images.githubusercontent.com/102302310/215272538-8aad13f5-b267-470e-a9bf-ed9e18798e02.jpg)

![4](https://user-images.githubusercontent.com/102302310/215272576-b57e10c4-4643-47f8-b1d9-7a10e4359516.jpg)

Client_2 – віртуальна машина, на якій розгорнуто ОС Linux CentOS

Інтерфейси підключені в режимі «Внутрішня мережа» до мереж Net3 та Net4 як показано на малюнку
![3](https://user-images.githubusercontent.com/102302310/215272694-357470c3-075d-4189-8c8b-8eede8af603e.jpg)

![4](https://user-images.githubusercontent.com/102302310/215272731-1b937db9-d67b-4f5a-a61c-eafc33cc3afb.jpg)

Адреса мережі Net2 – 10.94.16.0/24, 
Адреса мережі Net3 – 10.7.94.0/24, 
Адреса мережі Net4 – 172.16.16.0/24
1. На Server_1 налаштувати статичні адреси на всіх інтерфейсах.
![netplan](https://user-images.githubusercontent.com/102302310/215354396-c1fbda44-7c4c-4cc4-a88a-9d81be89febe.png)
![ip  a show](https://user-images.githubusercontent.com/102302310/215354397-f3e946a5-9657-406d-b544-1d2e62d048f9.png)

2. На Server_1 налаштувати DHCP сервіс, який буде конфігурувати адреси Int1 
Client_1 та Client_2

![dhcp](https://user-images.githubusercontent.com/102302310/215354620-06582c63-5ce3-47da-9517-7fe45bb7d8b3.png)

3. За допомогою команд ping та traceroute перевірити зв'язок між віртуальними 
машинами.  

 Server1 > Client1
![ping  Server1 to Client1](https://user-images.githubusercontent.com/102302310/215354394-e531b48a-6745-487d-a5b6-32661dfb18d2.png)
 Server1 > Client 2
![ping Server1 to Client2](https://user-images.githubusercontent.com/102302310/215354387-e8ea25bf-83a9-4b2a-ab79-0f6ce806e505.png)

Client1 > Client2
![ping  Client1  to Client2 ](https://user-images.githubusercontent.com/102302310/215355240-3e91ad35-95c1-4a57-bb05-7f6fdc4d7532.png)

traceroute Client1 > Client2
![traceroute Client1  to  Client2](https://user-images.githubusercontent.com/102302310/215355237-e3d5debb-cf7e-4924-84c8-c3939644342b.png)
![tracerout  Client1 to Client2](https://user-images.githubusercontent.com/102302310/215355239-745dc3f8-6558-4a1d-99a4-38c28eb1551d.png)
