# Using Jupyter Notebooks with Vesta

Jupyter Notebooks can be used as a way to access files & run code in Vesta.
It is a particularly useful way of doing exploratory data analysis and of
writing and debugging code, both due to the functionality of the notebooks and
because it allows you to see your files and write code in the browser on your
local machine.

You can find out more about Jupyter Notebooks
[here](http://jupyter.readthedocs.io/en/latest/index.html)

## On Vesta:

You must first open up Jupyter Notbooks in headless mode on the server using
the command: `jupyter notebook  --no-browser --port 8888`

IMPORTANT: The `8888` is a four-digit port number. To avoid port conflicts we
are setting up a document where you can each claim a port number. If multiple
users use the same port then it will result in conflicts. The number itself is
arbitrary but must be the same in all of these commands.

Please notify an admin when you choose a port number.

## On your local machine:

You must have Jupyter Notebooks installed locally. You can find instructions on
downloading the latest version [here](http://jupyter.readthedocs.io/en/latest/install.html)

You can now connect to the Notebook on your local machine using an ssh tunnel.

To connect to the notebook use the command:
`ssh -i ~/.ssh/your_private_key -f -N -L localhost:8888:localhost:8888 your_net_id@vesta.soc.cornell.edu`

You can then open up your browser and type `http://localhost.8888` to open the notebook
or alternatively if you are a Mac or Linux user type `open http://localhost.8888` into the command line to
automatically open it in your default browser.

You will see the directory where you ran the command on Vesta and can access files
as if you are logged into Vesta.

To help to speed this process up you can save these two commands in a text file and
run it as a shell script. You will need to change the permissions to make it
executable using `chmod 755 file_name`. You can then run the file in the command line by typing `./file_name`

##Troubleshooting
You may run into issues with the port on your local machine already being in use.
This can happen sometimes if you disconnect and then reconnect to the notebook
locally. To solve this you can kill the processes running on the port using the
command `sudo kill $(sudo lsof -t -i:8888)` but remember to use caution when
using `sudo`!

## Using in combination with screen:
To use it most efficiently you should also familiarize yourself with [screen](https://github.com/socdyn/wiki/blob/master/vesta/use_screen.md).
This will allow you to keep your notebook running and maintain your local
connection to Vesta even when you are not connected in the command line.
All you need to do is open a screen session on vesta, run the command to start
the headless notebook, and then detach from the screen session. This will
keep the headless notebook running in the background. It is still recommended
that you frequently save your work as any interruption of Vesta service may
cause your screen session to end.
