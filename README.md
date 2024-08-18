1. Write code for a simple user registration form for an event.

Aim: Write code for a simple user registration

===================================================================================================================================
Step 1: Create the Project Structure
Create the following files and directories:

Dockerfile
requirements.txt
app.py
templates/
register.html
success.html

====================================================================================================================================
Step 2: Dockerfile
Create a Dockerfile with the following content to create a Docker image for your Flask application:

dockerfile
Copy code
FROM python:3.8
WORKDIR /app
COPY . .
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 5000
CMD ["python", "app.py"]

======================================================================================================================================
Step 3: requirements.txt
Create a requirements.txt file with the following content to list the dependencies of your Flask application:

makefile
Copy code
Flask==1.1.2


=============================================================================================================
Step 4: app.py
Create an app.py file with the following code for a simple user registration form in Flask:

python
Copy code
from flask import Flask, request, render_template

app = Flask(__name__)

@app.route('/register', methods=['GET', 'POST'])
def register():
    if request.method == 'POST':
        name = request.form['name']
        email = request.form['email']
        password = request.form['password']
        # Store the user data in a database or file
        return render_template('success.html')

    return render_template('register.html')

if __name__ == '__main__':
    app.run(host='0.0.0.0')

=================================================================================================================
Step 5: Templates
Create a templates folder and add the following two files:

register.html

html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register</title>
</head>
<body>
    <form method="post">
        <input type="text" name="name" placeholder="Name" required>
        <input type="email" name="email" placeholder="Email" required>
        <input type="password" name="password" placeholder="Password" required>
        <input type="submit" value="Submit">
    </form>
</body>
</html>
success.html

html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Success</title>
</head>
<body>
    <h2>Registration Successful</h2>
</body>
</html>


=======================================================================================================================

Step 6: Build and Run the Docker Container
Build the Docker Image:

Open a terminal in the project directory and run the following command:

sh
Copy code
docker build -t simple-flask-app .
Run a Docker Container:

Run the container using the following command:

sh
Copy code
docker run -p 5000:5000 simple-flask-app
Access the Registration Form:

Open a web browser and go to http://localhost:5000/register to access the registration form.





Important Notes
This example is a basic demonstration and does not include security measures or proper error handling. For a production environment, consider implementing the following:

Password hashing (e.g., using werkzeug.security.generate_password_hash)
Input validation and sanitization
Proper error handling
Secure transport (HTTPS)






