# Create container
```
docker run -it -d --name=pass -h=pass -p 1022:22 cristo/password_manager /bin/bash
```

# SSH credentials (do not forget to change root password after first login by: passwd root
```
ssh root@localhost -p1022
password: root
```

# If you have not enough random bytes - you need to run this command on your host machine:
```
apt-get install -y rng-tools &&
rngd -r /dev/urandom
```

# Creating public key
```
gpg --gen-key 
```
Additional parameters:
```
Please select what kind of key you want:
   (1) RSA and RSA
```

```
What keysize do you want?
    4096
```

```
Key is valid for? 
    0
```

```
Email address: 
    pass@<your_company_domain.com>
```

# Initiate pass 
```
pass init pass@<your_company_domain.com>
```

# Git global parameters
```
git config --global user.email "user@mail.com"
```
```
git config --global user.name "Password Storage"
```
```
pass git init
```

# Add new password AWS api example with length 20
```
pass generate aws/project/stage/api/1 20
```
```
pass generate aws/project/prod/api/2 20
```

# Show all stored passwords location
```
pass list
```
Example output:
```
$ pass list
Password Store
├── aws
│   └── project
│       └── prod
│           └── api
│               └── 2

```

# Show aws/project/prod/api/2 password command:
```
pass show aws/project/prod/api/2
```
Example output:
```
$ pass list aws/project/prod/api/2
ZiFXK2\Bm2TL]\#zP&v*

```

# Update password command:
Remove old and generate new:
```
pass generate aws/project/prod/api/2 20
```
Remove old and type new:
```
pass insert aws/project/prod/api/2
```
Edit decrypted password from terminal editor:
```
pass edit aws/project/prod/api/2
```