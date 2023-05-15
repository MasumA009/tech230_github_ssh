# Using SSH on Github

### Step 1: Navigate 
Open GitBash as admin, navigate using `ls` and `cd` (more help on this can be found in my Git repo), navigate to the home directory. This can be checked by using 
```
pwd
```
mine is as follows:
![Alt text](images/Screenshot%202023-05-15%20161443.png)

### step 2: Search for .ssh file
to list all the files, use 
```
ls -a
```
this should list all the files. as in:
![Alt text](images/Screenshot%202023-05-15%20165705.png)
physically scroll and look for a file that ends in `.ssh`.

Rememeber this is like a keyring, it lists all the files, in the same place.

### Step 3: Create a .ssh file
If there is no `.ssh` file we need to create one, do so by:
```
mkdir .ssh
```

### Step 4: Generate public and private keys
To create the keys, use:
```
ssh-keygen -t rsa -b 4096 -C "masum.ali0326@gmail.com"
```
This should result in:
![Alt text](images/Screenshot%202023-05-15%20170329.png)

Enter the name of the key file,  and enter no pass phrase, confirm it through and it should look like this:
![Alt text](images/Screenshot%202023-05-15%20170240.png)

### Step 5: Create SSH key on github. 
We need to navigate to Github -> settings -> SSH and GPG keys:
![Alt text](images/Screenshot%202023-05-15%20170705.png)

Select new key, enter a title(maybe the same name as the file to avoid confusion). Keep it as an authenticator. 
However now we need a key to put in, we get this from the public key on Gitbash.

Use the following command to look into the public key
```
cat masum_github_ssh_test.pub
```
This should result in:
![Alt text](images/Screenshot%202023-05-15%20171012.png)

copy this key and place it in the key field on Github, 

### Step 6: Test the key (confirmation)
We need to check if the ssh link has worked, todo this we run:
```
ssh -T git@github.com
```
if this hasn't worked we need to do the next steps

### Step 7: run 
run the following:
```
eval `ssh-agent -s`
```
remember to use ` and not '. the backtick near number 1, 
```
ssh-add ~/.ssh/masum_github_ssh_test
```
shown in:
![Alt text](images/Screenshot%202023-05-15%20171847.png)
### step 8: Confirmation 
run step 6 again, 
```
ssh -T git@github.com
```
hopefullly resulting in: 
![Alt text](images/Screenshot%202023-05-15%20171915.png)