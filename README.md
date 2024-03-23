# Module-Linux-Networking
EPAM University Programs DevOps external course Module – Linux Networking

Server_1 - A virtual machine on which Linux is deployed. Int1 of this machine in 
in the "Network Bridge" mode is connected to the Net1 network, i.e. it is in the address space of the home network. 
address space of the home network. The IP address of Int1 is set statically in accordance with the address space. 
address space. The interfaces Int2 and Int3 respectively 
are connected in "Internal Network" mode to the networks Net2 and Net3.
![Снимок экрана (448)](https://user-images.githubusercontent.com/102302310/215271673-9657b562-1299-4046-bfbf-94a6bae76c3d.png)
![enp0s3](https://user-images.githubusercontent.com/102302310/215272209-e53e4cfc-ce33-4cd6-a182-02297c26c903.jpg)
![net2](https://user-images.githubusercontent.com/102302310/215272217-d10596da-a290-4361-90ba-2c87e83c4f84.jpg)
![net3](https://user-images.githubusercontent.com/102302310/215272226-46f761ec-0b86-4425-a718-18384fd46771.jpg)

Client_1 – a virtual machine on which the Linux Ubuntu operating system is deployed

The interfaces are connected in the "Internal Network" mode to the Net2 and Net4 networks as shown in the figure
![изображение_viber_2023-01-28_16-38-46-151](https://user-images.githubusercontent.com/102302310/215272538-8aad13f5-b267-470e-a9bf-ed9e18798e02.jpg)

![4](https://user-images.githubusercontent.com/102302310/215272576-b57e10c4-4643-47f8-b1d9-7a10e4359516.jpg)

Client_2 – a virtual machine on which the Linux CentOS operating system is deployed

The interfaces are connected in the "Internal Network" mode to the Net3 and Net4 networks as shown in the figure
![3](https://user-images.githubusercontent.com/102302310/215272694-357470c3-075d-4189-8c8b-8eede8af603e.jpg)

![4](https://user-images.githubusercontent.com/102302310/215272731-1b937db9-d67b-4f5a-a61c-eafc33cc3afb.jpg)

Network address Net2 – 10.94.16.0/24, 
Network address Net3 – 10.7.94.0/24, 
Network address Net4 – 172.16.16.0/24
1. On Server_1, configure static addresses on all interfaces.
![netplan](https://user-images.githubusercontent.com/102302310/215354396-c1fbda44-7c4c-4cc4-a88a-9d81be89febe.png)
![ip  a show](https://user-images.githubusercontent.com/102302310/215354397-f3e946a5-9657-406d-b544-1d2e62d048f9.png)

2. On Server_1, configure a DHCP service that will configure Int1 addresses 
Client_1 та Client_2

![dhcp](https://user-images.githubusercontent.com/102302310/215354620-06582c63-5ce3-47da-9517-7fe45bb7d8b3.png)

3. Use the ping and traceroute commands to check the connection between virtual machines 
virtual machines.  

 Server1 > Client1
![ping  Server1 to Client1](https://user-images.githubusercontent.com/102302310/215354394-e531b48a-6745-487d-a5b6-32661dfb18d2.png)
 Server1 > Client 2
![ping Server1 to Client2](https://user-images.githubusercontent.com/102302310/215354387-e8ea25bf-83a9-4b2a-ab79-0f6ce806e505.png)

Client1 > Client2
![ping  Client1  to Client2 ](https://user-images.githubusercontent.com/102302310/215355240-3e91ad35-95c1-4a57-bb05-7f6fdc4d7532.png)

traceroute Client1 > Client2
![traceroute Client1  to  Client2](https://user-images.githubusercontent.com/102302310/215355237-e3d5debb-cf7e-4924-84c8-c3939644342b.png)
![tracerout  Client1 to Client2](https://user-images.githubusercontent.com/102302310/215355239-745dc3f8-6558-4a1d-99a4-38c28eb1551d.png)

4. On the virtual interface lo Client_1, assign two IP addresses according to the following rule: 
172.17.D+10.1/24 та 172.17.D+20.1/24. 
Configure the routing so that traffic from Client_2 to 172.17.D+10.1 goes through Server_1, and to 172.17.D+20.1 through Net4. 
Use traceroute to test this.
D=16

172.17.26.1/24

172.17.36.1/24 

Client2 > 172.17.26.1 (via Server1 )
 
![1722](https://user-images.githubusercontent.com/102302310/215370580-f0c1b5fc-02e8-4777-9c6b-7c9d5e72cca8.jpg)

Client2 > 172.17.36.1 ( via Net 4 )

![172 17 36 1 cat](https://user-images.githubusercontent.com/102302310/215365663-85a572a5-a969-4766-ac3b-367a0b8dd378.jpg)

![172 36 1 1](https://user-images.githubusercontent.com/102302310/215365694-8a0c1825-64fc-45b7-883f-5edaa06f240e.jpg)

5.Calculate the shared address and summarizing mask of 172.17.26.1/24 and 172.17.36.1/24, with the prefix being as large as possible. 
                
172.17.26.1/24                                                            10101100.00010001.00011010.00000001


172.17.36.1/24                                                            10101100.00010001.00100100.00000001
___________________________________________________
172.17.0.0      10101100.00010001.00000000.00000000

255.255.192.0   11111111.11111111.11000000.00000000
___________________________________________________

common address and mask = 172.17.0.0/18

 Delete routes set in the previous step            
![5,0](https://user-images.githubusercontent.com/102302310/215371900-d247bc05-8651-4358-93fe-699c930c306f.jpg)

 Replace them with a merged route that should go via Server_1.    

![5,1](https://user-images.githubusercontent.com/102302310/215377586-641c140a-8f9d-4157-a0f8-8c784814d24c.jpg)

![1](https://user-images.githubusercontent.com/102302310/215379315-7bbb2994-53df-48da-b83b-1bd848b7386c.jpg)

![2](https://user-images.githubusercontent.com/102302310/215379318-ce07440d-2fb4-4b29-8d8d-52832e75ec49.jpg)

6. Configure the SSH service so that Client_1 and Client_2 can connect to Server_1 and to each other.

Client1 > Server1 

![SSH CL1 to SERVER1](https://user-images.githubusercontent.com/102302310/215547901-9c1c98e1-0f85-4d48-9d04-7531a67425cc.png)

Client2 > Server1

![2 to  s1](https://user-images.githubusercontent.com/102302310/215537703-a09834a0-92c7-42c6-8314-6db7166583bc.jpg)

Client2 > Client1 

![2  to  1](https://user-images.githubusercontent.com/102302310/215594984-5a027f51-dcea-4260-b3bc-e2dcb85353a5.jpg)

7.  Configure the firewall on Server_1 as follows:
•  SSH connection from Client_1 is allowed and denied from Client_2

![71](https://user-images.githubusercontent.com/102302310/215630857-632827ab-4af7-415a-8860-6efa65589dd4.jpg)
![7task](https://user-images.githubusercontent.com/102302310/215630590-1e8d5c25-58b8-42c5-9b42-5e513deca509.jpg)
![111111](https://user-images.githubusercontent.com/102302310/215631434-5a0e3967-b7db-4052-9634-4377f382b4bd.jpg)

• From Client_2 pinged on 172.17.26.1, but it didn't ping on 172.17.36.1
![ping input 172 17 0 0](https://user-images.githubusercontent.com/102302310/215633761-b28890ee-1ce4-42ae-96e1-45dd3fd2f3d5.jpg)
![iptables](https://user-images.githubusercontent.com/102302310/215634466-86843776-8c81-4c70-898f-8d3dfafe171c.jpg)
![iptables2](https://user-images.githubusercontent.com/102302310/215634470-408380a8-4d74-4f70-80ef-3c1390b9ab12.jpg)

8. On Server1, configure the NAT service so that Client1 and Client2 ping the Internet


![4](https://user-images.githubusercontent.com/102302310/215640903-ff30a1c3-0de2-4e10-a381-33d52153193e.jpg)
![5](https://user-images.githubusercontent.com/102302310/215640905-ebc1fcad-1716-414d-90cd-850719b8f679.jpg)
![1](https://user-images.githubusercontent.com/102302310/215639969-dd107018-dedd-405a-8691-41ad830800ec.jpg)
![2](https://user-images.githubusercontent.com/102302310/215639975-2ea843f2-66e4-40ed-833a-5e4a05b91461.jpg)
![3](https://user-images.githubusercontent.com/102302310/215639976-3bdb0144-817d-41a1-ac78-7d9a2ccf6398.jpg)
