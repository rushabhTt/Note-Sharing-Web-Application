# django-notes app
Notes Sharing App using django(python framework)

# PREREQUISITES
1.  Python Version >> 3.7.8
2.  Virtualenv setup
 
Original Features
1. A registerd user can access all the notes shared/added by the admin
2. Can download the pdfs
3. Admin can handle all the feattures like adding/updating/deleting the notes/users and can have overall control.
5. sqlite3 database

Modified Features:
1. Search by word functionality for logged-in users
2. API is used to fetch jokes from a button: "Are you bored?" for logged-in users

How to Run this project locally?

## Virtualenv Setup
1.    <code>python -m install virtualenv</code> or <code>pip install virtualenv</code> 
&nbsp;
3.    <code>virtualenv (environment_name)</code>
&nbsp;
5.    <code>.\(environment_name)\Scripts\activate</code> or On Unix or MacOS: <code>source (environment_name)/bin/activate</code>
&nbsp;

## Run Project
1.  First Locate to project folder in cmd with virtual environment running
&nbsp;
2.  <code>cd ./django-notesapp</code> then <code>pip install -r requirements.txt</code>
&nbsp;
3.  <code>python manage.py makemigrations</code>
&nbsp;
4.  <code>python manage.py migrate</code>
&nbsp;
5.  <code>python manage.py createsuperuser</code>
&nbsp;
6.  <code>python manage.py runserver</code>


Paste this <code>127.0.0.1:8000</code> IP Address on any browser and it will start.

<code>127.0.0.1:8000/admin</code> and enter your superuser's username/pass for django admin panel access

It's great that you're working on a note-sharing app using Django! Let's break down the steps to run your project locally:

## Prerequisites
1. **Python Version**: Ensure you have Python 3.7.8 or a higher version installed.
2. **Virtualenv Setup**: Set up a virtual environment for your project. You can do this by running the following commands:
    ```bash
    python -m venv environment_name
    ```
    Activate the virtual environment:
    - On Windows: `.\environment_name\Scripts\activate`
    - On Unix or MacOS: `source environment_name/bin/activate`

## Running the Project
1. **Navigate to Project Folder**: Open your command prompt or terminal and navigate to the project folder where your Django project is located.
2. **Install Dependencies**: Run the following command to install the required dependencies listed in `requirements.txt`:
    ```bash
    cd ./django-notesapp
    pip install -r requirements.txt
    ```
3. **Database Setup**:
    - Create the initial database schema by running:
        ```bash
        python manage.py makemigrations
        python manage.py migrate
        ```
    - Create a superuser (admin) account:
        ```bash
        python manage.py createsuperuser
        ```
4. **Run the Development Server**:
    ```bash
    python manage.py runserver
    ```
    This will start the development server, and you can access your app at `http://127.0.0.1:8000/`.

5. **Admin Panel**:
    - Access the Django admin panel at `http://127.0.0.1:8000/admin`.
    - Log in using the superuser's username and password.

Your note-sharing app should now be up and running!