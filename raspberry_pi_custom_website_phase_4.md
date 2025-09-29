# Phase 4: Build & Host Your Own Webpage on the Raspberry Pi

## Objective

Create your own custom webpage using any editor or IDE of your choice, then host it using your Raspberry Pi’s Flask server. This phase gives you creative freedom to design anything from a portfolio or fan page to a fun experiment. The key requirement is that your page must be hosted and viewable on your Pi.

## Why This Matters

You’re moving from following guided code to **creating your own project**. This will give you hands-on experience with HTML, CSS, and JavaScript, while learning how to serve and host static files from your own server.

## Part A — Create Your Webpage

1. Make a new folder for your project:
   ```bash
   mkdir -p ~/my-webpage
   ```
2. Inside that folder, create an `index.html` file. This is the entry point for your webpage.
3. Use any editor you prefer:
   - **Thonny** (already installed on the Pi)
   - **VS Code** (recommended for more advanced editing)
   - **Replit** or **CodeSandbox** (online editors)
   - Or even a simple text editor like notepad or notepad++

You can also add:

- `styles.css` for custom styling
- `script.js` for interactivity
- an `assets/` folder for images or other resources

## Part B — Create Your Flask Server File

1. Open the Terminal on your Raspberry Pi.

2. Navigate to your home directory (or wherever you want to keep the project):

   ```bash
   cd ~
   ```

3. Create a new file called `my_site.py`:

   ```bash
   nano my_site.py
   ```

4. Paste the following code inside the file:

   ```python
   from flask import Flask, send_from_directory

   app = Flask(__name__)

   WEB_DIR = "/home/pi/my-webpage"  # Path to your webpage folder

   @app.route("/")
   def index():
       return send_from_directory(WEB_DIR, "index.html")

   @app.route("/<path:filename>")
   def serve_files(filename):
       return send_from_directory(WEB_DIR, filename)

   if __name__ == "__main__":
       app.run(host="0.0.0.0", port=5000)
   ```

5. Save and exit Nano:

   - Press `CTRL + O`, then `Enter`
   - Press `CTRL + X`

6. Start the server:

   ```bash
   python3 my_site.py
   ```

7. Open a browser and go to:

   - `http://localhost:5000` (on the Pi)
   - `http://raspberrypi.local:5000` (from another device)
   - Or `http://<your Pi’s IP>:5000`

## Suggested Features

- A header with your name or page title
- A hero section with an image and caption
- Cards or sections for content (e.g., About, Gallery, Contact)
- Responsive design (looks good on phone and laptop)
- Optional: Interactive features with JavaScript

## Helpful Resources

- **W3Schools HTML/CSS/JS tutorials** — [https://www.w3schools.com/](https://www.w3schools.com/)
- **MDN Web Docs (Mozilla)** — [https://developer.mozilla.org/](https://developer.mozilla.org/)
- **freeCodeCamp Responsive Web Design** — [https://www.freecodecamp.org/learn/responsive-web-design/](https://www.freecodecamp.org/learn/responsive-web-design/)
- **Codecademy Learn HTML** — [https://www.codecademy.com/learn/learn-html](https://www.codecademy.com/learn/learn-html)
- **Traversy Media Crash Course (YouTube)** — [https://www.youtube.com/watch?v=UB1O30fR-EE](https://www.youtube.com/watch?v=UB1O30fR-EE)
- **HTML Crash Course for Absolute Beginners (YouTube)** — [https://www.youtube.com/watch?v=FazgJVnrVuI](https://www.youtube.com/watch?v=FazgJVnrVuI)

## Deliverables

1. The URL where your page is hosted (e.g., `http://raspberrypi.local:5000/`).
2. At least two screenshots:
   - Your webpage running in a browser
   - Your project folder showing `index.html` and other files
3. A short reflection (3–5 sentences): What did you build? What was fun? What would you add if you had more time?

## Grading Rubric (25 points)

- **Hosting (5 pts):** Webpage loads successfully from Flask.
- **Structure (5 pts):** Files are organized, and page uses proper HTML.
- **Design (5 pts):** Clear layout, readable text, and some attention to visuals.
- **Creativity (5 pts):** Shows effort and originality; not just boilerplate text.
- **Submission (5 pts):** Correct URL, screenshots, and reflection included.

## Tips

- Always save your files before refreshing the browser.
- Restart Flask after changing Python routes.
- If your Pi’s `.local` address doesn’t work, use the IP (`hostname -I`).
- Broken CSS/JS usually means the file isn’t in the right folder or the link path is wrong.

