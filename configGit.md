
Set our Git global username and email so Git can tag our commits with our identity:
```
git config --global user.name "Deepak"
git config --global user.email "codeepakghimire@gmail.com"
```

Check the current Git configuration values that are set:
```
git config --list
```

Generate a new SSH key using the ed25519 algorithm, with your email as a label:
```
ssh-keygen -t ed25519 -C "codeepakghimire@gmail.com"
```

Start the SSH agent in the background to manage your SSH keys:
```
eval "$(ssh-agent -s)"
```

Add your newly generated private SSH key to the agent so it can be used for authentication:
```
ssh-add ~/.ssh/id_ed25519
```
List all SSH keys currently added to the agent (to verify your key is loaded):
```
ssh-add -l
```

Show the contents of your public key, which you'll copy and add to your GitHub SSH keys:
```
cat ~/.ssh/id_ed25519.pub
```

Test the SSH connection to GitHub to verify that authentication works correctly:
```
ssh -T git@github.com
```
Display the remote URLs used in your Git project to see if you're using HTTPS or SSH:
```
git remote -v
```

Make Git automatically use SSH instead of HTTPS when cloning or using GitHub URLs:
```
git config --global url."git@github.com:".insteadOf "https://github.com/"
```

T