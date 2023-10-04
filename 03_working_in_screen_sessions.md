# Working with screen sessions
As in any device, whenever you turn off the power, you kill every process that was running. The same is for user working stations: if powered off, they will detatch any active <code>ssh</code> connection (*do you remember it?* If not, take a look [here](./01_bash_basics.md/#ssh-to-login-to-a-remote-machine-or-server)) and your running processes will be killed.

To overcome this issue, you can rely on the <code>screen</code> utility.

## Table of contents
* **[<code>screen</code> is a terminal multiplexer](#screen-is-a-terminal-multiplexer)**
* **[Create a new screen session](#create-a-new-screen-session)**

## Command cheat sheet
| Command | Description |
| --- | --- |
| [<code>screen -S</code>](#create-a-new-screen-session) | Create a new screen session with a meaningful name |

## <code>screen</code> is a terminal multiplexer
The <code>screen</code> GNU utility allows users to **create and work with multiple terminals** in parallel (terminal multiplexer). This lets processes run even when the window is not visible or when the <code>ssh</code> session is terminated.

Thus, when you run a command in a screen session, you can **resume** it whenever you like. This is particularly helpful when you run very long tasks or when you are dealing with an unstable connection (*sic*).

Overall, you can think of a screen session as a **virtual terminal** that you create directly into the remote working station or server or cluster. Thus, since it is expected that remote hosts does not go out (not always true, *sic<sup>2</sup>*), processes will continue to run as long as it takes.

## Create a new screen session
To create a new screen session, you just need to type <code>screen</code> on your terminal. That's it. A new terminal window will appear and you are already on your screen session.

By doing this, UNIX will assign to your screen just a random numerical identifier. Thus, it is advisable to create screen sessions with human-readable names, so that you can recall what you were doing in each of them.

To create a **screen session with a meaningful *<ins>S</ins>ession* name**, use the <code>-S</code> flag:

```bash
$ screen -S my_new_screen_session
```

To detach from a working screen session, 

[↑ Table of contents ↑](#table-of-contents)