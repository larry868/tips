# .bashrc & co

## .profile vs .bashrc vs .bash_profile

`.profile` is for things that are not specifically related to Bash, like environment variables PATH and friends, and should be available anytime. For example, `.profile` should also be loaded when starting a graphical desktop session.

`.bashrc` is for configuring the **interactive Bash usage**, like Bash aliases, setting your favorite editor, setting the Bash prompt, etc.

`.bash_profile` is for making sure that both the things in .profile and .bashrc are loaded for login shells. For example, `.bash_profile` could be something simple like

```bash
# simplest .bash_profile
. ~/.profile
. ~/.bashrc
```

If you were to omit .bashrc, only .profile would be loaded.

:warning: .bash_profile is executed for login shells: login via consol or ssh
