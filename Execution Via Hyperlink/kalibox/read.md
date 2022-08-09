Once the link in the document is clicked, the target system sends an authentication request to the attacking host. Since responder is listening on the other end, victim's NetNTLMv2 hash is captured:

![image](https://user-images.githubusercontent.com/73394656/183561954-bd6fe99f-5b25-415f-832d-0ccc6db09830.png)

The retrieved hash can then be cracked offline with hashcat:

```
hashcat -m5600 /usr/share/responder/logs/SMBv2-NTLMv2-SSP-10.0.0.2.txt /usr/share/wordlists/rockyou.txt --force
```
Success, the password is cracked:

![image](https://user-images.githubusercontent.com/73394656/183562048-7c81d558-8800-46d0-85db-6870d25d4efa.png)


Using the cracked passsword to get a shell on the victim system:

![image](https://user-images.githubusercontent.com/73394656/183562069-b2358e28-17dc-4435-a3c4-75a3048f2e6a.png)
