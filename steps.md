# Steps to Ansible Deployment

## Set up Ansible to run on local machine (MacOS or Linux)

```
git clone https://github.com/ProfessorKazarinoff/ansible-jupyterhub.git
cd ansible-jupyterhub
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
ansible --version
```

## Ensure you have a local SSH key

```
cat ~/.ssh/id_rsa.pub
# you should see output
```

if no local SSH key exists:
```
ssh-keygen
# accept default location
```

## Aquire DO OAuth Token

Sign up for a Digital Ocean account and into Digital Ocean. Select API from the left-hand menu. Under Tokens/Keys, generate a new personal access token. Copy the access token and save it in ```~/.do/do_api_token```

Without quotes, save the text of the api token in ```~/.do/do_api_token``` (no extension). Something like below:

```
as345dkjlk245dkjl345asad546aklj345
```

## Run test playbooks

```
ansible-playbook get_do_domain_names.yml
ansible-playbook get_do_SSH_key_info.yml
ansible-playbook put_do_SSH_key.yml
ansible-playbook get_do_account_info.yml
```

## Get DO SSH Keys

## Get DO Domain Names

## Create new DO server with SSH Keys

## Link Domain Name to DO Server

## Auto populate ansible invintory with new DO server

## Create non-root sudo user with password

## install miniconda

## create virtual env install jupyterhub

## Install Nginx

## Nginx Config

## JupyterHub systemd

## JupyterHub config

## Google OAuth

## Run JuyterHub
