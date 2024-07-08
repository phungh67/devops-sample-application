# Tables of contents

***
## 1. [Requirements](#1-requirements-1)
## 2. How to use
## 3. Containerization
## 4. Further ỉmprovement
***

# 1. Requirements

- ``python3``, ``python3-pip``, ``python3-venv``
- ``docker-ce``
- Allow traffic on ``TCP`` port ``5000`` if using AWS EC2 or ``ufw``

# 2. How to use

- Clone the repository with command ``git clone``.
- Create a new directory with name ``instance/config.py``
- Add these line into ``instance/config.py`` file:
    ```python
    # instance/config.py

    SECRET_KEY = 'abc' # input some secret here
    SQLALCHEMY_DATABASE_URI = 'lib:user:pass:IP:port:database' # input the connection URI for database
    ```
- Create and active the Python virtual environment
    ```bash
    python3.8 -m venv env
    env/bin/active
    ```
- Install necessary packages for application
    ```bash
    pip install -r requirements.txt
    ```
- Export environment variables
    ```bash
    export FLAKS_CONFIG=development
    export FLASK_APP=run.py
    ```
- Run application
    ```bash
    flask run
    ```

# 3. Containerization

Check the content of Dockerfile in this repository. This image is not hard-coded. All environment variables should be passed in run.

    ```bash
    docker build -t devops-journal/application .
    docker run -d --name application -p 3000:3000 -e "FLASK_CONFIG=development" -e "FLASK_APP=run.py" devops-journal/application
    ```

# 4. Further improvement

- Cache.
- Error handling.