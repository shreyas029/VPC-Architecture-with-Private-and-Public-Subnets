# VPC-Architecture-with-Private-and-Public-Subnets

This project provides practical, real world experience on how to setup and configure Virtual Private Cloud (VPC) with Public and Private subnets across two Availability Zones, the Public subnets host a NAT gateway for  internet access and a load balancer node to distribute traffic. Auto Scaling Group which dynamically scales the application based on the workload. The load Balancer distributes the traffic and access internet via NAT gateway.


## Creating and Configure VPC
![ss1](https://github.com/user-attachments/assets/15625637-8a70-4ff0-b011-71d40bbad9e9)
![ss2](https://github.com/user-attachments/assets/2cdd83ae-f5fe-40fa-8e2c-4dc1139971bc)

## Create Auto Scaling Group (ASG)
![ss3](https://github.com/user-attachments/assets/a539a358-5fe6-4ca3-a191-6e9dd026c109)
![ss4](https://github.com/user-attachments/assets/8e10b613-9196-48bd-b72c-f3e5f1a9377e)
![ss5](https://github.com/user-attachments/assets/f91f105f-dd84-43e1-a901-dcb3c0c2cd03)
![ss6](https://github.com/user-attachments/assets/4169d292-dba8-40d4-a73a-32774fd108f6)
![ss7](https://github.com/user-attachments/assets/04ca292f-f3ff-4a12-bae9-153dbabfc86c)

Template is created.

![ss8](https://github.com/user-attachments/assets/79c1282e-2920-42ff-bdd1-241f79255002)

![ss9](https://github.com/user-attachments/assets/2d9b83f7-acf4-4937-b748-b6c258b82e9e)
![ss10](https://github.com/user-attachments/assets/906cabb1-4b71-4d9b-8878-6df434cdf675)
![ss11](https://github.com/user-attachments/assets/433f1e43-e90f-4316-b74d-6f89b2146d5c)

Click on "Skip to Review" and select 'Create Auto Scaling Group'.
ASG has now been successfully created.

Under the Instances tab, there will be 2 instances running and the Auto Scaling Group has launched the instances in two different Availability Zones.
![ss12](https://github.com/user-attachments/assets/b353f23f-5103-42b1-8419-83cf8d3145c2)

## Creating Bastian Host
![ss13](https://github.com/user-attachments/assets/249927ae-3f29-440c-a96a-e7a99647c368)
![ss14](https://github.com/user-attachments/assets/22628b03-58b1-4d1a-9ad0-aa86b7e6daa5)
Launch the Instance.

### SSH to Private Instance

1. To connect to Private Instance, first thing to do is SSH to Bastian Host.
2. Download the PEM file in the Bastian Host, without this file it is not possible to SSH to Private Instance.
3. Open the Terminal on your Windows or Linux machine.
4. Use the <scp> command to copy the PEM file.

  ``` scp -i /Users/<username>/Downloads/<filename.pem> /Users/<username>/Downloads/<filename.pem> ubuntu@<Batian_Host IP>:/home/ubuntu``` 

  5. The above command will copy the PEM file from local machine to Bastian Host.
  6. Now SSH to the Bastian Host using the command.
     ```ssh -i <filename.pem> ubuntu@<Bastian Host IP>```
  7. Use 'dir' for Windows or 'ls' for Linux to list down the files in that directory.
  8. SSH to the Private Instance using the command.
  ```ssh -i <filename.pem> ubuntu@<private IP> ```
  9. Deply the application in one of the instance to test the Load Balancer.
  10. Create an HTML file using vim editor.
      ```vim <filename>.html```
  11. Inside the editor, paste this command.
![html code](https://github.com/user-attachments/assets/bea91d34-fa3c-444f-acb0-1a728be91779)

  12. To save the vim file, press Esc ->:w
      To quit, press Esc ->:q!
      To save and quit, press Esc ->:wq
  13. Start a Python HTTP server on port 8000 to deploy the application on the Private Instance.
```python3 -m http.server 8000```
  14. The application is deployed on port 8000.

## Creating the Load Balancer

![ss15](https://github.com/user-attachments/assets/42043623-f765-41da-8324-a34568a0e428)
![ss16](https://github.com/user-attachments/assets/f7671fd6-e491-4d15-bb19-bb4c784a55d2)
![ss17](https://github.com/user-attachments/assets/b38b989c-7e0b-4398-9e04-7f9329f318e9)
![ss18](https://github.com/user-attachments/assets/5d552830-8df9-4e33-bffd-36ffddf8fba9)
![ss19 specify port 8000](https://github.com/user-attachments/assets/fc05ab62-b115-43be-be57-380dc56b073e)
![ss20](https://github.com/user-attachments/assets/b29a0d33-491f-48da-89a1-ca56bf58e6ec)
![ss21](https://github.com/user-attachments/assets/43caa2d6-0ca5-4fd5-a1ca-c4fe9ca2de1d)
![ss22 mention target group in alb](https://github.com/user-attachments/assets/893ed0b7-b02a-4527-b3b9-713cc70f2f10)
![ss23](https://github.com/user-attachments/assets/5ae1b587-b39c-4c73-88c1-faf83e733b7b)

Copy the below DNS and paste it on browser.
![ss24 copy DNS name](https://github.com/user-attachments/assets/de870a1c-1bee-46ff-bccf-5787e6ef788e)
![ss25](https://github.com/user-attachments/assets/37cc9809-51dd-4792-a130-8f9d0b0f8cf4)

Successfully Deployed the application on Private Instance and can be accessed through internet using Load Balancer.

