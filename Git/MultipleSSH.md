# Objective

Working on your personal project and company project simultaneously? Then you will need to setup ssh for each. Here is how to do it in 5 steps.

# Step 1: Generating a new ssh key

You can generate a new ssh key with this command.

```
ssh-keygen -t rsa -C "email@example.com"
```

You would be prompt to enter the filename. It is recommended to set a separately name that you can recognize later, e.g. `personal`. Finally you would get a pair of private key (personal) and public key (personal.pub).

# Step 2: Adding the keys to your GitHub accounts

Login into your github account, go to the "Settings" page. Select "SSH and GPG keys" and save your ssh key.

# Step 3: Configuring the SSH config file

Go to your ./ssh folder and configure your computer to use different ssh file.

```
cd ~/.ssh
touch config
```

Inside the config file

```
Host github.com-personal
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_personal
  IdentitiesOnly yes
  User git

Host github.com-work
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_work
  IdentitiesOnly yes
  User git
```

# Step 4 Testing the SSH connection

Finally you can test the config by the following command

```
ssh -T git@github.com-personal
ssh -T git@github.com-work
```
