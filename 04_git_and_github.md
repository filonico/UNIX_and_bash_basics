**🚧🚧 WORK IN PROGRESS 🚧🚧**

**🚧🚧 WORK IN PROGRESS 🚧🚧**

**🚧🚧 WORK IN PROGRESS 🚧🚧**

## github basics - NOTES

We must link the github repository to our server repository (look [here](https://github.com/CompBio-Group/LINEs)).

You can add stuff at different moments and then push everything at the end.

Before pushing, you are asked a token to be generated.

We will just commit things, the admin will then push them.

To remove things we should use git rm.

This is the way to work on our repository. With shared repositories is different, because there can be version conflicts: so we should use branches.

Create new branch git co -b [the_name]

```bash
git pull
git add .
git commit -m "a message"
git push
# Remove directory already online
git rm -r --cached some-directory
git commit -m 'Remove the now ignored directory "some-directory"'
git push origin master
```

I would like to thank **[jacopoM28](https://github.com/jacopoM28)** for sharing his knowledge about the use of git with our group!