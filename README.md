# wedding_gift
This is a draft for my personal project. Where newly weds can choose what they want for their wedding and streamline the gifts according to them.
Outline of how I can implement this app/website along with a suggested architecture:
1. Core Functional Requirements:

    QR Code Scan: The QR code will link guests to the website.
    Item List: Display a list of items (e.g., fridge, TV, etc.) that the couple wants.
    Gift Selection: Guests can mark an item as "purchased."
    Verification of Purchase: Guests upload a photo of the purchased item for verification.
    Image Processing: Use image recognition to verify if the uploaded image matches the item on the list.
    Remove Purchased Items: If verified, the item gets removed from the list.

2. High-Level Architecture:
Frontend:

    Technologies: HTML/CSS/JavaScript, React (or Vue.js, Angular) for a modern, responsive design.
    Features:
        Landing page with a wedding theme.
        List of gift items that updates in real-time when items are purchased.
        Upload form for guests to upload images for verification.
        Notifications (for you and guests) confirming successful purchase verification.

Backend:

    Technologies: Python (with Flask/Django for the web server), or Node.js.
    Features:
        API to serve the list of items.
        Logic to update the list when an item is purchased.
        Handle image uploads and pass them for image processing.
        Manage session data for guests (QR code tokens, etc.).

Database:

    Technologies: PostgreSQL/MySQL/MongoDB.
    Features:
        Store item list with status (available/purchased).
        Store uploaded images for verification.
        Track guests who made purchases.
        Schema:
            Items Table: Name, Description, Image URL, Status.
            Purchases Table: Guest Info, Item, Purchase Date, Uploaded Image.

Image Processing (Verification):

    Technologies: Python with OpenCV or TensorFlow (for basic image classification).
    Features:
        When a guest uploads a photo, use image processing to compare it with an existing image of the item.
        If the image matches (within a certain threshold), mark the item as purchased.
        Notify the guest and update the item list.

Cloud/Hosting:

    Technologies: AWS/GCP/Azure, or simpler options like Heroku or Firebase.
    Features:
        Host the frontend and backend.
        Use cloud storage (S3, Google Cloud Storage) to store images.
        Use cloud services for image processing if needed.

3. Workflow:

    QR Code Scanning:
        The guest scans the QR code, which directs them to the website (e.g., www.weddinggifts.com/yourwedding).

    Gift Selection:
        They browse a list of gifts on the website.
        After selecting an item, they can upload an image of the purchased item.

    Image Verification:
        The backend receives the image and compares it with stored reference images of the items.
        Python (with OpenCV or TensorFlow) processes the image to check for a match.
        If the match succeeds, the item is marked as purchased, and the website removes the item from the available list.

    Real-time Updates:
        The website updates the gift list in real-time (you can use WebSockets or polling).
        You (the couple) receive notifications for purchases.

4. Tools and Technologies:

    Frontend:
        React.js (for the UI)
        HTML5/CSS3 (for design)
        QR code generator (to create and link the QR code)
    Backend:
        Python (Flask or Django) or Node.js
        APIs for gift listing, purchase, and verification logic
        Libraries: OpenCV (image comparison), TensorFlow (optional, for advanced verification)
    Database:
        PostgreSQL or MySQL (for relational data) or MongoDB (if you want a more flexible schema).
    Cloud Services:
        AWS S3 (for image storage)
        AWS Lambda or Google Cloud Functions (for serverless image processing)
    Deployment:
        Heroku (easy deployment) or AWS/GCP (scalable solution).

5. Implementation Steps:

    Frontend Development:
        Create a simple React app with a list of items.
        Add QR code generation logic for the invitations.

    Backend Development:
        Create an API to serve the gift list and accept image uploads.
        Set up a Python-based image recognition system.

    Image Processing:
        Set up OpenCV or TensorFlow to recognize the images.

    Database & Real-time Updates:
        Create the database schema and connect it to the backend.
        Use WebSockets or polling to update the gift list in real-time.

    Deployment:
        Deploy the site on a cloud platform and connect it with the QR code for invitations.

6. Potential Challenges:

    Image Verification Accuracy: You might need to fine-tune your image processing algorithm for accuracy.
    Scalability: Ensure that the server can handle multiple users uploading images and checking the gift list.

Final Note:

This project involves both software development (front-end, back-end) and image processing. Depending on your skill set, you might want to focus on the simpler features first (gift list management, QR code scanning) and add image recognition later. You can also start with a basic manual confirmation system for gift purchases before automating the image processing fully.
