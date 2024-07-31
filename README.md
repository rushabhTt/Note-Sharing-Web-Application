# django-notes app
Notes Sharing App using django(python framework)

## Loom video link:
https://www.loom.com/share/cf8414d2f9e343af8b0ba0f7f03ef705?sid=66343ea5-52eb-4745-9395-383b4c27248a
https://www.loom.com/share/f1080d1a080b4ded90d4b267207ab617?sid=4efac753-6476-43ee-8c85-3f5de97141a4

# PREREQUISITES
1.  Python Version >> 3.7.8
2.  Virtualenv setup
 
### Original Features
1. A registerd user can access all the notes shared/added by the admin
2. Can download the pdfs
3. Admin can handle all the feattures like adding/updating/deleting the notes/users and can have overall control.
5. sqlite3 database

### Modified Features:
1. Search by word functionality for logged-in users
2. API is used to fetch jokes from a button: "Are you bored?" for logged-in users

## How to Run this project locally? (Follow following instructions)

<!-- ## Virtualenv Setup
1.    <code>python -m install virtualenv</code> or <code>pip install virtualenv</code> 
&nbsp;
3.    <code>virtualenv (environment_name)</code>
&nbsp;
5.    <code>.\(environment_name)\Scripts\activate</code> or On Unix or MacOS: <code>source (environment_name)/bin/activate</code>
&nbsp; -->

<!-- ## Run Project
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
6.  <code>python manage.py runserver</code> -->


<!-- Paste this <code>127.0.0.1:8000</code> IP Address on any browser and it will start.

<code>127.0.0.1:8000/admin</code> and enter your superuser's username/pass for django admin panel access -->


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
1. **Navigating to Project Folder and Installing Dependencies**: Open your command prompt or terminal and navigating to the project folder where our Django project is located to Install Dependencies: Run the following command to install the required dependencies listed in `requirements.txt`:
    ```bash
    cd ./django-notesapp
    pip install -r requirements.txt
    ```
2. **Database Setup**:
    - Create the initial database schema by running:
        ```bash
        python manage.py makemigrations
        python manage.py migrate
        ```
    - Create a superuser (admin) account:
        ```bash
        python manage.py createsuperuser
        ```
3. **Run the Development Server**:
    ```bash
    python manage.py runserver
    ```
    This will start the development server, and you can access your app at `http://127.0.0.1:8000/` IP Address on any browser.

4. **Admin Panel**:
    - Access the Django admin panel at `http://127.0.0.1:8000/admin`.
    - Log in using the superuser's username and password.

Your note-sharing app should now be up and running!

## Deployment Guide for AWS Lambda with Zappa

This guide provides step-by-step instructions for deploying a Django application to AWS Lambda using Zappa. It also includes setting up an S3 bucket for file uploads and updating the application's URLs to work with the Lambda function's URL.

### Prerequisites

- Python 3.6 or later
- Django application setup
- AWS CLI configured with appropriate credentials
- Zappa installed (`pip install zappa`)

### Steps

### 1. Install Zappa

First, ensure that Zappa is installed in your virtual environment. You can install it using pip:

```bash
pip install zappa
```

### 2. Configure AWS S3 Bucket

Create an S3 bucket to store uploaded files:

1. Go to the [AWS S3 console](https://console.aws.amazon.com/s3/).
2. Click on "Create bucket."
3. Choose a unique bucket name and select a region.
4. Configure bucket settings as needed and click "Create bucket."

### 3. Update Django Settings

In your Django project's `settings.py`, configure the following settings for media file uploads to S3:

Bucket can also be made by zappa automatically we have to make it available to read to make it accessible by the project.

```python
# AWS_ACCESS_KEY_ID = 'your-access-key'
# AWS_SECRET_ACCESS_KEY = 'your-secret-key'
AWS_STORAGE_BUCKET_NAME = 'your-bucket-name'
AWS_S3_CUSTOM_DOMAIN = f'{AWS_STORAGE_BUCKET_NAME}.s3.amazonaws.com'

DEFAULT_FILE_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
STATICFILES_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
MEDIA_URL = f'https://{AWS_S3_CUSTOM_DOMAIN}/media/'
```

Ensure you have the `django-storages` package installed:

```bash
pip install django-storages boto3
```

### 4. Initialize Zappa

In the root of your Django project, initialize Zappa:

```bash
zappa init
```

Follow the prompts:

- **AWS region:** Select your preferred AWS region.
- **S3 bucket:** Enter the name of your S3 bucket.
- **Django settings:** Specify the path to your `settings.py` file (e.g., `your_project.settings`).
- **Other settings:** Use default values unless you have specific requirements.

This command creates a `zappa_settings.json` file in your project root.

### 5. Update URLs for Lambda

In your Django settings or views, update any URLs or API routes to match your new Lambda function's URL. You can find the URL after deploying the function.

### 6. Deploy the Lambda Function

Deploy your Django application to AWS Lambda using Zappa:

```bash
zappa deploy dev
```

Zappa will package your application, create a Lambda function, and deploy it. Note the provided URL, which will be your new endpoint for the Django application.

### 7. Update API Endpoints

If your application uses hard-coded URLs for API endpoints, update them to use the new Lambda function URL. This ensures that project interact with the deployment.

### 8. Managing Media Files

Since media files are stored in S3, ensure your Django admin panel and any other file upload functionalities point to the correct S3 URLs.

### 9. Updating and Managing the Lambda Function

To update your Lambda function after making changes to your Django application:

```bash
zappa update dev
```

To manage your deployment, use:

- **`zappa status`**: Check the status of the deployed application.
- **`zappa tail`**: View logs in real-time.

### 10. Cleanup

To remove the Lambda function and associated resources:

```bash
zappa undeploy dev
```

## Conclusion

This README provides the essential steps to deploy a Django application to AWS Lambda using Zappa. For more advanced configurations and features, refer to the [Zappa documentation](https://github.com/Miserlou/Zappa) and AWS Lambda best practices.
