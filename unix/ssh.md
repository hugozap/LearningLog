# SSH Tips

## Mount SSH folder using sshfs

sudo sshfs -o allow_other,defer_permissions user@host:/ ~/local_mount_folder/

-o defer_permissions : If the remote user can write, then the local mount point will be writtable too.

## Use different key for a site:

In ~/.ssh/config

Host dev
    HostName test.com
    Port 8888
    User test
Host github.com
    IdentityFile ~/.ssh/github.key
    