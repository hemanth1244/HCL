1.Get me the IP address of a particular domain (guvi.in). How do I find my CPU/memory usage of my server?. Test the connectivity between 2 nodes?
<img width="1016" height="954" alt="image" src="https://github.com/user-attachments/assets/311be7ce-0dd5-471f-be8a-9d87ccbc2bee" />

<img width="1257" height="955" alt="image" src="https://github.com/user-attachments/assets/0022343f-b706-47b2-88a8-ab810572f2ed" />

<img width="1108" height="237" alt="image" src="https://github.com/user-attachments/assets/5aa3d137-02cc-4426-b298-f7cdf738c06e" />

C. Test connectivity between 2 nodes
1. Using ping (basic check)
   <img width="730" height="161" alt="image" src="https://github.com/user-attachments/assets/3ae00c24-0e25-484a-91eb-4d69fea6d6ab" />
   
2. Using traceroute (path check)
  <img width="634" height="186" alt="image" src="https://github.com/user-attachments/assets/60dcbb9a-22d8-4dc8-a823-cf5a889937f7" />

3. Using netcat (port-level connectivity)
   <img width="860" height="375" alt="image" src="https://github.com/user-attachments/assets/03964920-dd41-4840-a9f5-951111111718" />

2. App Running but Page Not Loading (guvi.com:9000)
netstat -tulnp | grep 9000
B. Check if the port is open locally
nc -zv localhost 9000
C. Check firewall rules (VERY common issue)
<img width="800" height="605" alt="image" src="https://github.com/user-attachments/assets/01accce4-25b9-49be-aa91-85e9163f7a55" />

![Uploading image.png…]()




      

   




