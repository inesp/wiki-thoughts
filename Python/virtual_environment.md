# Virtual Environment

The purpose of Virtual environment is to create a selfcontained sandox
for your projects, to isolate them from the each other and from your
system's global set-up. 

Using them has 2 pleasant consequences:
- You have no problems when 2 projects each need a different version 
of the same library, because each version is accessible only by its 
owning project.
- It is easy to share your project. You need to share only the project folder.
And you team mate only needs to call
```bash
virtualenv env
source env/bin/activate
pip install -r requirements.txt
```
to set up the project.

## How to set up a virtual environment

Set up virtualenv for Python3.6:
```bash
virtualenv -p /usr/bin/python3 env
```

This creates an `env`-folder to where is saves all dependencies.

Activate the virtualenv:
```bash
source env/bin/activate
```

The name of the current virtual environment will now appear on the left of the 
prompt (e.g. (env)Your-Computer:your_project UserName$) to let you know that 
it’s active. From now on, any package that you install using pip will be 
placed in the my_project folder, isolated from the global Python installation.

When you're done with the virtual env call:
```bash
deactivate
```

To delete a virtual environment, just delete its folder. 
(In this case, it would be `rm -rf env`.)

While developing you can call `pip install <whatever>` and after that from time
to time you should call:
```bash
pip freeze > requirements.txt
```

This creates the requirements.txt with a list of requirements.
But it seems the freeze puts a lot of items into the file. If I call 
`pip install request` it fills the requirements.txt file with every 
sub-package the request needs. This might be redundant. Or not :)

**You should NOT commit the virtualenv to GIT, but you should commit the 
requirements.txt.**

When cloning the project to somewhere new you should call:
```bash
virtualenv env
source env/bin/activate
pip install -r requirements.txt
```
