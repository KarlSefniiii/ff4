<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <style>
        body { text-align: center; font-family: Arial, sans-serif; }
        .gallery { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
        .gallery img { width: 150px; height: 100px; cursor: pointer; border: 2px solid transparent; }
        .gallery img:focus, .gallery img:hover { border-color: blue; outline: none; }
        .preview { margin-top: 20px; width: 300px; height: 200px; border: 2px solid black; background-size: cover; background-position: center; }
    </style>
</head>
<body onload="initGallery()">
    <h1>Interactive Photo Gallery</h1>
    <div class="preview" id="imagePreview">Hover or focus on an image below</div>
    <div class="gallery">
        <img src="image1.jpg" alt="Description 1" tabindex="0">
        <img src="image2.jpg" alt="Description 2" tabindex="0">
        <img src="image3.jpg" alt="Description 3" tabindex="0">
        <img src="image4.jpg" alt="Description 4" tabindex="0">
        <img src="image5.jpg" alt="Description 5" tabindex="0">
        <img src="image6.jpg" alt="Description 6" tabindex="0">
    </div>
    <script>
        function updatePreview(event) {
            document.getElementById("imagePreview").style.backgroundImage = `url(${event.target.src})`;
        }
        
        function resetPreview() {
            document.getElementById("imagePreview").style.backgroundImage = "none";
        }
        
        function initGallery() {
            console.log("Gallery initialized");
            let images = document.querySelectorAll(".gallery img");
            
            images.forEach(img => {
                img.addEventListener("mouseover", updatePreview);
                img.addEventListener("mouseleave", resetPreview);
                img.addEventListener("focus", updatePreview);
                img.addEventListener("blur", resetPreview);
            });
        }
    </script>
</body>
</html>
