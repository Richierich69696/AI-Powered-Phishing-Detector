# AI-Powered-Phishing-Detector
AI powered phising detector 
README.md

AI-Powered Phishing Detector

Hey, I’m Raj —got my Master’s in Info Systems and Security, and I’m obsessed with outsmarting cyber crooks. This project’s my baby: a tool that sniffs out phishing emails using AI. Picture those sketchy “Your account’s hacked—click here!” emails. I wanted something that learns to spot ‘em like a pro, and here’s how I pulled it off.

What’s the Big Idea?

Phishing emails trick folks into spilling passwords or cash—nasty stuff. My tool uses AI to read emails and yell, “Fake!” or “Safe!” It’s like training a dog to bark at strangers, but for your inbox.

How I Made It Happen

Alright, let’s break this down like I’m telling you over coffee:

1. Grabbing Emails: I hunted down two stacks—real ones and fakes. Think legit Amazon receipts (“Your order shipped!”) vs. phishing junk (“Urgent! Pay $500 now!”). I nabbed safe fakes from PhishTank—great spot for test data.
   Example: Real: “Hi [Your Name], your subscription’s renewed.” Fake: “Bank alert—click to verify!”

2. Turning Words into Clues: AI doesn’t get words, so I counted stuff like “urgent” or “click.” Say an email’s “Urgent! Click here!”—I made it [1, 1, 0] (urgent: 1, click: 1, boring words: 0).
   Macro Detail: This is “Bag of Words”—like tallying how often a crook says “now” to scare you.

3. Training the AI: I fed my word counts to the AI and said, “See this? Phishing. That? Safe.” After 50 emails, it started spotting patterns—like fakes love “urgent.”
   Example: It learned “Pay now or lose access” smells fishy.

4. Testing It Out: I tossed it a new email—“Your prize awaits, click!”—and it screamed “Phishing!” Nailed it.
   Macro Detail: The AI’s a “Naive Bayes” model—fancy name for a guesser that gets smarter with practice.

Stuff You’ll Need

Python: Free download from python.org. It’s like the hammer for this build.
Helpers:
- scikit-learn—the AI brain.
- pandas—keeps emails organized.
  
Your Laptop: No rocket ship required—just your everyday machine.

Emails: Start with 10 real ones (your inbox) and 10 fakes (PhishTank or make some up).


Let’s Build It—Step by Step with Commands

1. Set Up Python: Hit python.org, download the latest version (like 3.11), run the installer. Check “Add Python to PATH” during setup—super important!
   Command to check it worked: Open your command line (Windows: type “cmd” in search, hit enter; Mac: type “terminal” in spotlight) and type “python --version”. You’ll see something like “Python 3.11.2”—if not, reinstall.

2. Get the Helpers: In your command line, type these one by one and hit enter after each:
   - “pip install scikit-learn” (grabs the AI brain—takes a sec).
   - “pip install pandas” (gets the organizer—quick download).

3. Make a Folder: On your desktop, right-click, New > Folder, name it “PhishingDetector”. Open it.
   Command to get there: In command line, type “cd Desktop\PhishingDetector” (Windows) or “cd ~/Desktop/PhishingDetector” (Mac) and hit enter.

4. Code It: Open Notepad (Windows) or TextEdit (Mac), paste this, save as “phish_detector.py” in your folder:
```python

# My little phishing catcher
emails = ["Order confirmed, thanks!", "Urgent! Click to save your account!"]
labels = ["safe", "phishing"]

from sklearn.feature_extraction.text import CountVectorizer
vectorizer = CountVectorizer()  # Turns words into numbers
email_numbers = vectorizer.fit_transform(emails)

from sklearn.naive_bayes import MultinomialNB
model = MultinomialNB()  # The AI brain
model.fit(email_numbers, labels)

# Test it
new_email = ["Win $1000, click now!"]
test_numbers = vectorizer.transform(new_email)
result = model.predict(test_numbers)
print("Phishing!" if result[0] == "phishing" else "Safe!")

Run It: Back in command line (after “cd” to your folder), type “python phish_detector.py” and hit enter. You’ll see “Phishing!” pop up—sweet!
Bumps in the Road

Tiny Emails: “Hi” alone confuses it—needs more meat to chew on.
Not Enough Data: 5 emails? Meh. 50? Gold. Beg or borrow more samples.
English Only: Spanish phishing? It’ll flail—stick to one language for now.

Why I Love It
This thing’s a scam-buster with AI smarts. Shows off my auditing chops—catching fakes is my superpower.
