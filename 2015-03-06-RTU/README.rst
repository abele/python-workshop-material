Setup
=====

Development environment
-----------------------
Visit https://koding.com/. Fill up sign up form.
Choose your username.
You will receive confirmation code in you e-mail.
Turn on the VM. VM startup time takes up to 5 min.

When active you can access your VM from outside at http://username.koding.io/.
This information is available from drop down menu in left hand side.

Make sure that `apt-get` is up to date::

  sudo apt-get update

Revision Control
----------------

Follow instruction at https://help.github.com/articles/generating-ssh-key
For current purpose, choose key without password::

  ssh-keygen -t rsa -C "your_email@example.com"

Open and copy content of `~/.ssh/id_rsa.pub` into GitHub 
https://github.com/settings/ssh.

Configure your `git`::

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

Project
-------

Create `python-workshop` project directory in `Application` directory.
Change current directory to project directory::

  cd Applications/python-workshop/


In GitHub create new repository and follow steps provided for new repository::

  echo "# python-workhop" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git remote add origin git@github.com:abele/python-workhop.git
  git push -u origin master

Now you project should show up in your GitHub account.

Python
------

Install `virtualenv` and `pip`::

  sudo aptitude install python-virtualenv python-pip


Activate project environment::

  source venv/bin/activate

Application
===========

Create `requirements.txt` file with web application development framework
library::

  Flask

You can find documentation at http://flask.pocoo.org/.
Install all projects requirements by running pip command::

  pip install -r requirements.txt

Add simple Flask application::

  from flask import Flask
  app = Flask(__name__)

  @app.route("/")
  def hello():
      return "Hello World!"

  if __name__ == "__main__":
      app.run(debug=True, host='0.0.0.0')


From terminal run application::

  python web.py


Inspect commands output for errors. See if it works at http://username.koding.io:5000/

Good job. Add changes to repository and push them::

  git add .
  git commit -m "Add Flask world application"
  git push
