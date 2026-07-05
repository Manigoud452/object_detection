# Object-Detection Photo Gallery

A Flask + PyTorch web app that turns uploaded photos into a searchable, 
Instagram/Pinterest-style gallery — powered by a pretrained Faster R-CNN 
(ResNet-50) object detection model.

## What it does

1. **Upload a photo** through the home page.
2. **Detect objects** in it — pick a specific object class (person, dog, car, 
   bottle, etc. — 90 COCO classes supported) or "all", and set a confidence 
   threshold.
3. The app runs the image through Faster R-CNN, draws bounding boxes around 
   matching objects, and saves each detected object as its own cropped image.
4. **Browse your gallery** — view all your uploads, or drill into a specific 
   object category to see every cropped instance of it across your photos.

## Tech stack

- **Backend:** Flask (Python)
- **ML model:** torchvision's pretrained Faster R-CNN for object detection
- **Image processing:** OpenCV, Pillow
- **Frontend:** HTML/CSS (Jinja2 templates), no JS framework
- **Deployment:** Dockerfile + docker-compose for containerized runs

## Running locally

\`\`\`bash
cd app
pip install -r requirements.txt
python app.py
\`\`\`
Visit http://localhost:8080

## Running with Docker

\`\`\`bash
cd app
docker compose up --build
\`\`\`

## Project structure

\`\`\`
app/
├── app.py              # Flask app + object detection logic
├── requirements.txt    # Python dependencies
├── templates/          # HTML pages (upload, results, galleries)
├── static/css/         # Stylesheets
├── uploads/            # User-uploaded photos (runtime)
├── objects/            # Cropped detected-object images (runtime)
├── Dockerfile
└── docker-compose.yml
\`\`\`
