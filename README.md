# Ex.07 Design of Interactive Image Gallery

## AIM
  To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS

## Step 1:

Clone the github repository and create Django admin interface

## Step 2:

Change settings.py file to allow request from all hosts.

## Step 3:

Use CSS for positioning and styling.

## Step 4:

Write JavaScript program for implementing interactivit

## Step 5:

Validate the HTML and CSS code

## Step 6:

Publish the website in the given URL.

## PROGRAM

## gallery.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Fav</title>
    <link rel="stylesheet" href="gallery.css">
</head>
<body>
    <h1>My Boys</h1>

    <div class="gallery" onclick="openLightbox(event)">
        <img src="neymar-1.png"
            alt="Neymar Jr.">
        <img src="ronaldo-2.png"
            alt="Cristiano Ronaldo">
        <img src="messi-3.png"
            alt="Lionel Messi">
        <img src="mbappe-4.png"
            alt="Kylian Mbappe">
    </div>

    <div id="lightbox">
        <span id="close-btn" onclick="closeLightbox()">&times;</span>

        <img id="lightbox-img" src="" alt="lightbox image">

        <div id="thumbnail-container">
        </div>
        <button id="prev-btn" onclick="changeImage(-1)">&lt; Prev</button>
        <button id="next-btn" onclick="changeImage(1)">Next &gt;</button>
    </div>
    <script src="gallery.js"></script>

</body>
</html>
```
## gallery.css
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Fav</title>
    <link rel="stylesheet" href="gallery.css">
</head>
<body>
    <h1>My Boys</h1>

    <div class="gallery" onclick="openLightbox(event)">
        <img src="neymar-1.png"
            alt="Neymar Jr.">
        <img src="ronaldo-2.png"
            alt="Cristiano Ronaldo">
        <img src="messi-3.png"
            alt="Lionel Messi">
        <img src="mbappe-4.png"
            alt="Kylian Mbappe">
    </div>

    <div id="lightbox">
        <span id="close-btn" onclick="closeLightbox()">&times;</span>

        <img id="lightbox-img" src="" alt="lightbox image">

        <div id="thumbnail-container">
        </div>
        <button id="prev-btn" onclick="changeImage(-1)">&lt; Prev</button>
        <button id="next-btn" onclick="changeImage(1)">Next &gt;</button>
    </div>
    <script src="gallery.js"></script>

</body>
</html>
```
## gallery.js
```
let currentIndex = 0;
        const images = document.querySelectorAll('.gallery img');
        const totalImages = images.length;

       
        function openLightbox(event) {
            if (event.target.tagName === 'IMG') {
                const clickedIndex = Array.from(images).indexOf(event.target);
                currentIndex = clickedIndex;
                updateLightboxImage();
                document.getElementById('lightbox').style.display = 'flex';
            }
        }

       
        function closeLightbox() {
            document.getElementById('lightbox').style.display = 'none';
        }

        
        function changeImage(direction) {
            currentIndex += direction;
            if (currentIndex >= totalImages) {
                currentIndex = 0;
            } else if (currentIndex < 0) {
                currentIndex = totalImages - 1;
            }
            updateLightboxImage();
        }

        
        function updateLightboxImage() {
            const lightboxImg = document.getElementById('lightbox-img');
            const thumbnailContainer = document.getElementById('thumbnail-container');

            
            lightboxImg.src = images[currentIndex].src;

            
            thumbnailContainer.innerHTML = '';

            
            images.forEach((image, index) => {
                const thumbnail = document.createElement('img');
                thumbnail.src = image.src;
                thumbnail.alt = `Thumbnail ${index + 1}`;
                thumbnail.classList.add('thumbnail');
                thumbnail.addEventListener('click', () => updateMainImage(index));
                thumbnailContainer.appendChild(thumbnail);
            });

            
            const thumbnails = document.querySelectorAll('.thumbnail');
            thumbnails[currentIndex].classList.add('active-thumbnail');
        }

        
        function updateMainImage(index) {
            currentIndex = index;
            updateLightboxImage();
        }

        updateLightboxImage();


        
        document.addEventListener('keydown', function (e) {
            if (document.getElementById('lightbox').style.display === 'flex') {
                if (e.key === 'ArrowLeft') {
                    changeImage(-1);
                } else if (e.key === 'ArrowRight') {
                    changeImage(1);
                }
            }
        });

              
        document.addEventListener('DOMContentLoaded', function() {
            let currentIndex = 0;
            const images = document.querySelectorAll('.gallery img');
            const totalImages = images.length;

          
            
            
            document.addEventListener('keydown', function(e) {
                if (document.getElementById('lightbox').style.display === 'flex') {
                    if (e.key === 'ArrowLeft') {
                        changeImage(-1);
                    } else if (e.key === 'ArrowRight') {
                        changeImage(1);
                    } else if (e.key === 'Escape') {
                        closeLightbox();
                    }
                }
            });

            
            updateLightboxImage();
        });
```



## OUTPUT

![alt text](<Screenshot 2026-05-26 182745.png>)

## RESULT
  The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
