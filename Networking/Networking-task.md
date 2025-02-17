# EC2 instance hosting NGINX using a Custom Domain

I will demonstrate the process of creating an EC2 instance running NGINX and how to link it to a custom domain that has been purchased via CLoudflare.

---

## 1: Purchase a Domain
I went on the [Cloudflare](https://www.cloudflare.com) website, created an account and purchased a domain. I called this domain `yahyam.co.uk`


## 2: Create an EC2 intance
Next, i went on the [AWS Management Console](https://aws.amazon.com/) website, created an account and navigated to **EC2** under the section called **Compute**. I then configured the instance by doing the following:

- Amazon Machine Image(AMI): **Ubuntu**
- Instance type: **t2 micro** for simplicity
- Instance details: Confirmed the **Public IP** was enabled
- Configure key pair: Selected **created new key pair** and called it 'my-key.pem'. The private key was then downloaded. This will be used in conjunction with **SSH** later.
- Security group: Selected **HTTP(port 80)** and **SSH(port 22)**

For the other settings, i left it as default. The instance can now be launched!


## 3: Connect to the instance.
I opened a new **terminal** on my machine and changed permissions on the `my-key.pem` file that was downloaded using `sudo chmod 400`.
```
sudo chmod 400 /Downloads/my-key.pem
```
Note: The private key was inside my **Downloads** folder.

---

Once the instance is running, i will **SSH** into the instance using the `my-key.pem` private key and the **Public IP Address** of the instance:
```
ssh -i /Downloads/my-key.pem ubuntu@3.8.125.215
```



## 4: Install and start NGINX

First i will update the instance. This will keep my system up-to-date with security patches & new versions.
```
sudo apt update && sudo apt upgrade -y
```

`apt update`: This updates the package list from Ubuntu’s repositories.

`apt upgrade -y`: This installs available updates for installed packages.

Next, i will install **NGINX**
```
sudo apt install nginx -y

```

I will then start and enable **NGINX** so that it auto boots on start.
```
sudo systemctl enable nginx
sudo systemctl start nginx
```

## 5: Verify **NGINX** is running
After waiting a few minutes for **NGINX** to complete its installation, i verified if it's running by typing my EC2's **Public IP Address** into a new browser.
```
http://3.8.125.215
```

This confirmed that NGINX was running successfully as it returned the **NGINX default welcome page**


<img width="718" alt="image" src="https://github.com/user-attachments/assets/19c39a39-d546-4018-997b-4164d849320b" />


## 6: Add an A record to Cloudflare
I navigated back to the **Cloudflare** website, clicked on the **DNS settings** section and added an **A record** to point to the EC2 instance using the **Public IP Address**. I set the record as `nginx.yahyam.co.uk`. This allowed me to access the NGINX server through my custom domain.


## 7: Test Custom Domain
Once i setup the **A record**, i tested my custom domain(`nginx.yahyam.co.uk`) to confirm if it's working as intended. After two minutes for the DND propagation, i opened a new browser and i successfully managed to access the NGINX default page via the custom domain. 


## 8: Verify using the `dig` command
I took further step to confirm if everything is in order by using the `dig` command to identify if the custom domain was correctly pointing to my EC2 instance.
```
dig nginx.yahyam.co.uk
```

Tis

