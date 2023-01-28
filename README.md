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

Client_1 та Client_2 – віртуальна машина, на якій розгорнуто ОС Linux  Ubuntu
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
