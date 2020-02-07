# Steps to Ansible Deployment

## Set up Ansible to run on local machine (MacOS or Linux)

```text
git clone https://github.com/ProfessorKazarinoff/ansible-jupyterhub.git
cd ansible-jupyterhub
python -m venv venv    # use python 3.6+
source venv/bin/activate
pip install -r requirements.txt
ansible --version
```

## Ensure you have a local SSH key

```text
cat ~/.ssh/id_rsa.pub
# you should see output
```

if no local SSH key exists:

```text
ssh-keygen
# accept default location
cat ~/.ssh/id_rsa.pub
```

## Aquire DO OAuth Token

Sign up for a Digital Ocean account and sign into Digital Ocean. Select API from the left-hand menu. Under Tokens/Keys, generate a new personal access token. Copy the access token and save it in ```~/.do/do_api_token```

Without quotes, save the text of the api token in ```~/.do/do_api_token``` (no extension). Something like below:

```text
as345dkjlk245dkjl345asad546aklj345
```

## Run test playbooks

Run the test playbooks to make sure the Digital Ocean oauth token works.

```text
ansible-playbook jupyterhub_setup0.yml
```

All of the variables you saved should be printed out and the location of the Digital Ocean Oauth Key should be shown.

## Fill in variables in vars/local.yml and vars/host.yml

The ```vars/default.yml``` file can be copied and saved as ```vars/local.yml``` and ```vars/host.yml```. Values in the vars are needed to set up the playbooks.

## Run the first set of Ansible playbooks to set up the server, install Jupyterhub, and get up to SSL cirts.

```text
ansible-playbook jupyterhub_setup1.yml
```

After this playbook runs, the server should be setup, but it may take time for the domain name to switch over. This may take a 5 minutes or 30 minutes. You should see the server IP address and ID number. Add the IP address to ```hosts``` under the header ```[jh_servers]```.

## Run the second set of Ansible playbooks to get an SSL cirtficut and configure nginx

```text
ansible-playbook jupyterhub_setup2.yml
```

After this is done, log into the server with the name jupyterhub and the password included in vars/host.yml. Make sure that PAM login works and notebooks can be run.

## Get Google Auth Credentials

Go through the process of getting a google_oauth_credentials.json file from developers.google.com. I couldn't figure out a way to automate this step. Save the credentials.json file in vault/google_oauth_credentials.json

## Run the next set of Ansible Playbooks

```text
ansible-playbook jupyterhub_setup3.yml
```
 
## Yeah! Now jupyterhub should be set up.

Sure there is work left to be done to build out the Ansible playbooks in a more logical way. They could be broken into roles and better organized. That will have to be the next deployment.
