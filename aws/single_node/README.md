In order to use Python 3, 'Software Collections must be installed,
therefore you must run `scl_repo` before `python3`

In order to switch to python3, ssh into the instance and run:
`scl enable rh-python36 bash` however this must be done each time you
login onto the machine. Alternatively, if you need to use Python 3 specifically
change shell commands to start as `python3` to run Python 3 apps.