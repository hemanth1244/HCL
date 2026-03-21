Create a simple script file and push it to repo. Create a project in Jenkins connected to your GitHub repository. When a commit is made to your repo, automatically build must get triggered from Jenkins and the output must be shared to me via email.
<img width="1683" height="749" alt="image" src="https://github.com/user-attachments/assets/4a791159-f836-429d-8fc9-3d01a03c226f" />
<img width="856" height="41" alt="image" src="https://github.com/user-attachments/assets/a9fb9421-dbdc-47ad-bd77-8732aee749bb" />
<img width="1133" height="65" alt="image" src="https://github.com/user-attachments/assets/669a25a8-cf41-4a41-9546-209dedbc633e" />
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
<img width="1459" height="595" alt="image" src="https://github.com/user-attachments/assets/f5deec03-10c3-4933-8136-f795e36dda01" />
<img width="996" height="65" alt="image" src="https://github.com/user-attachments/assets/460f7502-cbe7-4160-996c-882850e02c85" />
<img width="1884" height="929" alt="image" src="https://github.com/user-attachments/assets/9956aca8-0298-479c-adc5-cc666465b7e7" />
<img width="1377" height="862" alt="image" src="https://github.com/user-attachments/assets/c971edfb-c78d-45e6-8b30-7727444ea0c4" />
<img width="731" height="127" alt="image" src="https://github.com/user-attachments/assets/5edaf400-5af7-4342-9190-c7788280e04d" />
<img width="817" height="79" alt="image" src="https://github.com/user-attachments/assets/fcdf452c-4427-4f9d-b74d-405ce42ca203" />














