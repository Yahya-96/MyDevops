# EC2 instance hosting NGINX using a Custom Domain

I will demonstrate the process of creating an EC2 instance running NGINX and how to link it to a custom domain that has been purchased via CLoudfare.

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

First i will update the system. This will keep my system up-to-date with security patches & new versions.
```
sudo apt update && sudo apt upgrade -y
```

`apt update`: This updates the package list from Ubuntu’s repositories



