# User_Registration-Flask

Setting up a development environment

# Clone the code repository into ~/dev/my_app

mkdir -p ~/dev

cd ~/dev

git clone https://github.com/KARISHMASHINDE/User_Registration-Flask.git

# Create the 'my_app' virtual environment

mkvirtualenv -p PATH/TO/PYTHON my_app

# Install required Python packages

cd ~/dev/my_app

workon my_app

pip install -r requirements.txt

Flask-MySQLdb provides MySQL connection for Flask.

Quickstart

First, install Flask-MySQLdb:

$ pip install flask-mysqldb

Flask-MySQLdb depends, and will install for you, recent versions of Flask (0.12.4 or later) and mysqlclient. Flask-MySQLdb is compatible with and tested on Python 2.7, 3.5, 3.6 and 3.7.

Next, add a MySQL instance to your code:

from flask import Flask

from flask_mysqldb import MySQL

app = Flask(__name__)

app.config['MYSQL_HOST'] = 'localhost'

app.config['MYSQL_USER'] = 'root'

app.config['MYSQL_PASSWORD'] = ''

app.config['MYSQL_DB'] = 'User'

mysql = MySQL(app)

@app.route('/')

def users():
    cur = mysql.connection.cursor()
    
    cur.execute('''SELECT user, host FROM mysql.user''')
    
    rv = cur.fetchall()
    
    return str(rv)

if __name__ == '__main__':

    app.run(debug=True)
