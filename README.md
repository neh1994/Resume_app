# Resume_app
Creating a Python application to host your resume involves several steps. You can use Flask (a lightweight Python web framework) to serve your resume as a web page. This is a simple way to display your resume online. Below is a step-by-step guide to help you create a basic Python web application to host your resume.

### 1. **Install Flask**

First, make sure you have Python installed on your system. Then, you need to install Flask, which will serve as the web framework.

You can install Flask using `pip`:

```bash
pip install flask
```

### 2. **Create the Directory Structure**

Create a new directory for your project and set up the necessary files:

```
resume-website/
│
├── app.py
├── templates/
│   └── resume.html
├── static/
│   └── resume.pdf  # Optional, if you want to provide a downloadable PDF
└── README.md
```

- **`app.py`**: This is the main Python file where the Flask application will be configured.
- **`templates/`**: This directory will contain your HTML files.
- **`static/`**: This directory will store static files like images, CSS, and downloadable files (like your resume in PDF format).

### 3. **Create Your Flask Application (app.py)**

In the `app.py` file, write the following code to create a basic Flask application that serves your resume:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def home():
    return render_template("resume.html")

if __name__ == "__main__":
    app.run(debug=True)
```

- This code creates a Flask app and defines a route (`/`) that renders an HTML file (`resume.html`) when accessed.

### 4. **Create Your Resume HTML Template (resume.html)**

In the `templates/` directory, create the `resume.html` file. This is where you will write the HTML content of your resume. Here's an example template:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Name - Resume</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        h2 {
            color: #333;
        }
        .section {
            margin-bottom: 20px;
        }
        .contact-info {
            font-style: italic;
        }
        .download {
            display: block;
            text-align: center;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <h1>Your Name</h1>
    <p class="contact-info">Email: youremail@example.com | Phone: 123-456-7890 | Location: Your City, Country</p>

    <div class="section">
        <h2>Objective</h2>
        <p>Your objective statement goes here.</p>
    </div>

    <div class="section">
        <h2>Experience</h2>
        <ul>
            <li>
                <strong>Job Title 1</strong> - Company Name (Year - Year)
                <p>Job description and achievements.</p>
            </li>
            <li>
                <strong>Job Title 2</strong> - Company Name (Year - Year)
                <p>Job description and achievements.</p>
            </li>
        </ul>
    </div>

    <div class="section">
        <h2>Education</h2>
        <ul>
            <li>
                <strong>Degree 1</strong> - University Name (Year - Year)
                <p>Details about your degree and courses.</p>
            </li>
            <li>
                <strong>Degree 2</strong> - University Name (Year - Year)
                <p>Details about your degree and courses.</p>
            </li>
        </ul>
    </div>

    <div class="section">
        <h2>Skills</h2>
        <ul>
            <li>Skill 1</li>
            <li>Skill 2</li>
            <li>Skill 3</li>
        </ul>
    </div>

    <div class="download">
        <p><a href="{{ url_for('static', filename='resume.pdf') }}" target="_blank">Download PDF Version</a></p>
    </div>

</body>
</html>
```

### 5. **Optional: Add a Downloadable Resume (PDF)**

If you want to make your resume available for download as a PDF, place your PDF file in the `static/` folder (e.g., `static/resume.pdf`). The link to download the PDF is added in the `resume.html` using Flask's `url_for` function.

### 6. **Run Your Flask Application**

To run your Flask app, open a terminal, navigate to the project directory, and execute the following command:

```bash
python app.py
```

This will start a development server, and you should see something like this:

```bash
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

Visit `http://127.0.0.1:5000/` in your web browser, and you should see your resume displayed as a web page.

### 7. **Deploy Your Resume Online**

To make your resume available online, you can deploy your Flask application using platforms like:
- **Heroku**: Simple and free for small projects.
- **PythonAnywhere**: Another option for hosting small Python applications.
- **DigitalOcean, AWS, or other cloud platforms**: For more control over the deployment environment.

### Example of Deploying on **Heroku**:

1. **Install Heroku CLI** if you don’t have it already.
2. In your project directory, create a `requirements.txt` file (which lists all dependencies):

   ```bash
   flask==2.2.3
   ```

   Generate it with the following:

   ```bash
   pip freeze > requirements.txt
   ```

3. Create a `Procfile` to tell Heroku how to run your app:

   ```
   web: python app.py
   ```

4. Initialize a Git repository in your project directory (if you haven't already):

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

5. Log in to Heroku and create a new app:

   ```bash
   heroku login
   heroku create your-app-name
   ```

6. Push your project to Heroku:

   ```bash
   git push heroku master
   ```

7. Open your app in the browser:

   ```bash
   heroku open
   ```

Your resume should now be live on the web!

### Conclusion

This is a simple way to create a Python-based web application to host your resume using Flask. You can extend it with more features like a contact form, a portfolio, or a blog if desired. You can also style it using CSS frameworks like Bootstrap for a more polished look.
