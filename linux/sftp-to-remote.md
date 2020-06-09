## How to transfer files from local to a remote server via SFTP

### Upload files to the remote server
1. `sftp user@remoteIpAddress`
2. Enter credentials
3. To send a file from local, say `hello.txt`:
`put /local/path/to/hello.txt /target/server/directory`

To see the current directories of
local: `lpwd` # lists the current path of your computer
remote: `pwd` # lists the current path of the remote server you're connected to

### To download files from the remote server
1. Follow seteps 1-2 above.
2. `get /file/you/want.txt target/dir/in/local`

