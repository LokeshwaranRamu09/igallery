# Ex.08 Design of Interactive Image Gallery
## Date:26-12-24

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> GALLERY</title>
    <style>
        body {
            font-family:Georgia, 'Times New Roman', Times, serif;
            margin: 0;
            padding: 0;
            background-color: rgb(72, 14, 230);
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
        }

        .title {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 42px;
            font-style: oblique;
            color: rgb(11, 208, 54);
            text-shadow: 2px 2px 4px rgba(166, 233, 8, 0.6);
        }

        .gallery-container {
            display:grid;
            grid-template-columns: repeat(auto-fill, minmax(370px, 1fr));
            gap: 20px;
            padding: 20px;
            max-width: 1200px;
            width: 100%;
            margin-bottom: auto;
            margin-top: 10%;
        }

        .gallery-item {
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .gallery-item img {
            max-width: 110%; 
            height: 300px; 
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(146, 11, 20, 0.1);
            transition: transform 0.3s ease;
        }

        .gallery-item img:hover {
            transform: scale(1.40);
            cursor: pointer;
        }

        .slider {
            display: none;
            position: fixed;
            z-index: 2;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 120%;
            text-align: center;
        }

        .slider img {
            width: 100%;
            max-width: 700px;
            border-radius: 10px;
            transition: opacity 0.5s ease;
        }

        .arrow {
            cursor:all-scroll;
            position:relative;
            top: 60%;
            transform: translateY(-50%);
            font-size: 40px;
            color: rgb(13, 181, 64);
            user-select: none;
            padding: 10px;
        }

        .arrow.left {
            left: 10px;
            color: rgb(198, 240, 13);
        }

        .arrow.right {
            right: 10px;
            color: rgb(173, 192, 6);
        }

        .arrow:hover {
            color: rgb(15, 189, 18);
        }

        .close-btn {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background-color: rgba(244, 10, 10, 0.6);
            color: rgb(209, 238, 20);
            border: none;
            padding: 10px;
            cursor: pointer;
            font-size: 30px;
            border-radius: 5px;
            display: none; /* Initially hidden */
        }

        .close-btn:hover {
            background-color: rgba(202, 202, 13, 0.8);
        }

        footer {
            width: 100%;
            background-color: rgb(210, 20, 29);
            color: rgb(189, 220, 14);
            text-align: center;
            padding: 10px;
            font-size: 25px;
            position: absolute;
            font-weight: 600;
            font-style:inherit;
            bottom: 0;
        }
    </style>
</head>
<body>
    <div class="title"> GALLERY</div> 
    
    <div class="gallery-container">
        <div class="gallery-item">
            <img src="v1.jpeg" alt="Image 1">
        </div>
        <div class="gallery-item">
            <img src="v2.jpeg" alt="Image 2">
        </div>
        <div class="gallery-item">
            <img src="v3.jpeg" alt="Image 3">
        </div>
        <div class="gallery-item">
            <img src="v4.jpeg" alt="Image 4">
        </div>
        <div class="gallery-item">
            <img src="v5.jpeg" alt="Image 5">
        </div>
        <div class="gallery-item">
            <img src="v6.jpeg" alt="Image 6">
        </div>
    </div>

    <div class="slider" id="slider">
        <button class="close-btn" id="close-btn">&#10006;</button>
        <span class="arrow left" id="prev">&#10094;</span>
        <img src="" alt="Slider Image" id="slider-img">
        <span class="arrow right" id="next">&#10095;</span>
    </div>

    <footer>
       Created by R Lokeshwaran
    </footer>

    <script>
        const images = document.querySelectorAll('.gallery-item img');
        const slider = document.getElementById('slider');
        const sliderImg = document.getElementById('slider-img');
        const prevBtn = document.getElementById('prev');
        const nextBtn = document.getElementById('next');
        const closeBtn = document.getElementById('close-btn');

        let currentIndex = 0;
        images.forEach((image, index) => {
            image.addEventListener('click', () => {
                slider.style.display = 'block';
                sliderImg.src = image.src;
                currentIndex = index;
                closeBtn.style.display = 'block';
            });
        });

        prevBtn.addEventListener('click', (e) => {
            e.stopPropagation(); 
            currentIndex = (currentIndex - 1 + images.length) % images.length;
            sliderImg.src = images[currentIndex].src;
        });

        nextBtn.addEventListener('click', (e) => {
            e.stopPropagation(); 
            currentIndex = (currentIndex + 1) % images.length;
            sliderImg.src = images[currentIndex].src;
        });

        closeBtn.addEventListener('click', (e) => {
            e.stopPropagation(); 
            slider.style.display = 'none';
            closeBtn.style.display = 'none'; 
        });

        slider.addEventListener('click', () => {
            slider.style.display = 'none';
            closeBtn.style.display = 'none'; // Hide the close button
        });
    </script>
</body>
</html>
```

## OUTPUT:
![Screenshot 2024-12-26 162548](https://github.com/user-attachments/assets/ceb988d9-3f2e-45c2-a292-81bab7dfdf65)

![Screenshot 2024-12-26 161100](https://github.com/user-attachments/assets/4244e790-97f5-4489-aae6-01c5ac4a2eb0)

## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
