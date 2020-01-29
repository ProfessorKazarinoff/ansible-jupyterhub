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

## Aquire DO OAuth Token

Log into Digital Ocean and select API from the left-hand menu. Under Tokens/Keys, generate a new personal access token. Copy the access token and save it in ```~/.do/credentials```

```
# ~/.do/credentials
export DO_API_TOKEN="as345dkjlk245dkjl345a546aklj345k"
```

Save the ```credentials``` file and source it.

```
source ~/.do/credentials
echo $DO_API_TOKEN
```

## Run test playbooks

```
ansible-playbook get_do_domain_names.yml
ansible-playbook get_do_SSH_key_info.yml
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
