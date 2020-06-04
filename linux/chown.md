The linux operating system has a feature that allows many users to interact with its filesystem.

Because of this, many users can "own" files in the system. fileA is "owned" by userA, fileB "owned" by userB, etc.

The concept of ownership defines what user can do what with a file or directory.

Each file belongs to a User and a Group.

When a file is created, the file belongs to the User and the User's current Group. 

You can add more owners of that file by assigning more Users to that Group. 

Users and Groups have names and unique identifiers (UID for users, GID for Groups).

to see groups, type `groups`
to get a list of groups and their ids, type `id`, `id -u`, `id -nu`, `id -g`, `id -ng`


By default, the Group name is the same as the User's name when that User was created in the system.

## chown

You can use `chown` to change the files owner. You can:

- change the user
- change the group
- both at the same time

*NOTE*:

- the owner can change group ownership
- BUT only root can change user ownership, because that involves another user

## y tho

Why would you change ownership of a file?

- when you copy files from one linux/unix-like operating system to another, you need to change ownership so the receivers can access it too.
- a user may leave the organization
- authoring a script to be used by a specific user
- creating a file logged in as root, but want it to be accessible to a specific user


## Practical examples

### changing owner of file hello.js to user tae
`sudo chown tae hello.js`
`ls -l`

### changing several files at once
`sudo chown tae hello.js hey.js yo.js`
`ls -l`

### wildcards: all files that start with 'h'
`sudo chown tae h*.*`
`ls -l`

### directories
`sudo chown tae ./archive`
`ls -l -d ./archive`

### all files in directory and its children
`sudo chown -R tae ./archive`

### changing group ownership -- put a colon ':' + group name after the user name
`sudo chown tae:dortmunders lol.py`
`sudo chown tae: lol.py` -- shorthand to assign the current user's group



src: https://www.howtogeek.com/438435/how-to-use-the-chown-command-on-linux/
