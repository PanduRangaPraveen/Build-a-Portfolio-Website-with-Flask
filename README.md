from flask import Flask, render_template, request

app = Flask(__name__)  # Corrected

@app.route("/")
def home():
    return render_template("index.html")

@app.route("/contact", methods=["GET", "POST"])
def contact():
    if request.method == "POST":
        name = request.form["name"]
        email = request.form["email"]
        message = request.form["message"]
        # Here you can save to database or send email if needed
        return f"Thank you {name}, your message has been received!"
    return render_template("contact.html")

if __name__ == "__main__":  # Corrected
    app.run(debug=True)
