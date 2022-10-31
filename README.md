# BMKT670.V60-72020-Fall2022-Wedge-Project-Compute-Engine

# How to setup Compute Engine to run Wedge Project in the CLOUD

## Enable Compute Engine

<img width="484" alt="image" src="https://user-images.githubusercontent.com/35873877/198894756-c81630c4-8e5a-410b-a8ce-a2b76e2951b1.png">

Python is single threaded, so picking a VM with high memory and low core count is good.

https://cloud.google.com/compute/docs/instances
https://cloud.google.com/compute/docs/cpu-platforms#x86_processors

## Create Instance

<img width="579" alt="image" src="https://user-images.githubusercontent.com/35873877/198894853-60c99b5b-b490-4341-8927-961d647c038f.png">

Be VERY Careful when selecting intance types!! Costs can add up quickly if not being careful

<img width="382" alt="image" src="https://user-images.githubusercontent.com/35873877/198894893-baf4c11d-4dff-460f-acc1-8532810b3ae8.png">

For this project, selecting C2 machine is a good balance of speed and power

<img width="838" alt="image" src="https://user-images.githubusercontent.com/35873877/198895022-8e52fed2-c240-40d2-8391-a37eb1e313b0.png">

### Select Instance Type

Pick a c2-standard-4

<img width="580" alt="image" src="https://user-images.githubusercontent.com/35873877/198895045-1d94f891-86e9-4d93-a2c7-7e224f55eac0.png">

DO NOT LEAVE IT RUNNING WHEN NOT IN USE

<img width="375" alt="image" src="https://user-images.githubusercontent.com/35873877/198895065-b41574bb-5f94-4559-b0cd-4a6b9af9983e.png">

### Setup internal storage

#### Select SSD for optimal performance

<img width="931" alt="image" src="https://user-images.githubusercontent.com/35873877/198895166-7d420c21-7864-4d52-a370-f05e31f2fdfe.png">


#### Change Bootdisk size to 60GB

<img width="618" alt="image" src="https://user-images.githubusercontent.com/35873877/198895181-681fb516-3a29-44a0-af18-d5516f4fca28.png">

** It's an option to select Windows, but I'm more comfortable with Debian. **


### Enable Access to Google Big Query

<img width="320" alt="image" src="https://user-images.githubusercontent.com/35873877/198895244-4a70947d-1ec1-4d2f-80ab-7bc010819377.png">

### Enable Firewall Access to access jupyter notebook

<img width="451" alt="image" src="https://user-images.githubusercontent.com/35873877/198895257-d0417e45-d57f-44cb-9ffb-44c81f0bdb70.png">

## Create Instance

This Compute Instance may fall under a free trial, no promises

<img width="515" alt="image" src="https://user-images.githubusercontent.com/35873877/198895357-efac34a6-0feb-45c5-8e5f-2724b4bf58f6.png">

#### Wait for instance to boot

<img width="680" alt="image" src="https://user-images.githubusercontent.com/35873877/198895395-883ed798-3988-4bc3-9df3-7876609797c5.png">

### Connect via SSH

<img width="608" alt="image" src="https://user-images.githubusercontent.com/35873877/198895456-e91917ec-aceb-463e-be31-7064ba1c17ff.png">

This is an SSH Terminal

<img width="913" alt="image" src="https://user-images.githubusercontent.com/35873877/198895466-7b39a8eb-dc6e-42d8-9522-b59af6573157.png">


## Setup Python 3

https://www.how2shout.com/linux/install-python-3-x-or-2-7-on-debian-11-bullseye-linux/

```
sudo apt install python3 python-is-python3 -y
```

## Jupyter Notebook Setup

https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-debian-9

### Install Pip and Python Headers

```
sudo apt update
```

```
sudo apt install python3-pip python3-dev git curl -y
```

### Install Jupyter

```
pip install jupyter
```

** Close SSH Window and Reopen from Google Console **

## Run Jupyter Notebooks
```
jupyter notebook --ip=0.0.0.0 --allow-root
```

<img width="901" alt="image" src="https://user-images.githubusercontent.com/35873877/198896105-1c6b1fe8-c804-4d7c-b937-e4a79446ff47.png">


## Connecting to Jupyter Notebook

### All Users ###

Open port 8888 in the firewall

https://cloud.google.com/vpc/docs/using-firewalls

https://console.cloud.google.com/networking/firewalls/list

<img width="954" alt="image" src="https://user-images.githubusercontent.com/35873877/198896290-f31dcc9c-1675-4f08-adab-f3983b30cb12.png">

Create a rule to allow traffic to port 8888

<img width="576" alt="image" src="https://user-images.githubusercontent.com/35873877/198896335-4eeee4e7-8d1f-4d11-bffb-072921ad12d8.png">

For best practice only allow your IP address https://ipchicken.com/ 

<img width="569" alt="image" src="https://user-images.githubusercontent.com/35873877/198896381-98787277-cda6-4e14-8e8d-f99c782b8848.png">

Results
<img width="656" alt="image" src="https://user-images.githubusercontent.com/35873877/198896420-094f5601-23c2-4987-8ad5-cd4e9a2ecb72.png">

Get your Esxternal IP address from the Compute Engine Screen

<img width="1170" alt="image" src="https://user-images.githubusercontent.com/35873877/198896454-e715e1ad-b3b6-4632-9192-41c61968fc6d.png">

If everything worked

<img width="787" alt="image" src="https://user-images.githubusercontent.com/35873877/198896481-c555b869-3e02-46b7-b86f-c60b450c4b90.png">

To get your token check your SSH Console

<img width="906" alt="image" src="https://user-images.githubusercontent.com/35873877/198896496-67d997dd-beb1-4e78-af7b-3089082c9041.png">

The default path is the folder you launched jupyter notebooks from, so in most cases the home folder and will be empty.




### Mac Users ###

ssh -L 8888:localhost:8888 your_server_username@your_server_ip

### Windows Users ###

https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-debian-9#step-5-connect-to-the-server-using-ssh-tunneling







