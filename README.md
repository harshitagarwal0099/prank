<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prank Website</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f1f1f1;
            padding: 20px;
        }

        #video {
            border: 5px solid #3498db;
            width: 80%;
            height: 400px;
        }

        #canvas {
            display: none;
            margin-top: 20px;
        }

        #capture-btn {
            padding: 10px 20px;
            font-size: 18px;
            background-color: #3498db;
            color: white;
            border: none;
            cursor: pointer;
            margin-top: 20px;
        }

        #monkey-photo {
            display: none;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <h1>welcometo my Website</h1>
    <p>Click below to open your camera and take a picture.</p>
    <p>"Upload your photo to see your next life!"</p>

    <video id="video" autoplay></video>
    <canvas id="canvas"></canvas>
    <br>

    <button id="capture-btn">Capture Photo</button>
    <br>
    
    <img id="monkey-photo" src="https://media.newyorker.com/photos/59095bb86552fa0be682d9d0/master/pass/Monkey-Selfie.jpg" width="300" alt="Monkey Photo">

    <script>
        const videoElement = document.getElementById('video');
        const canvasElement = document.getElementById('canvas');
        const captureButton = document.getElementById('capture-btn');
        const monkeyPhoto = document.getElementById('monkey-photo');

        // Initialize the camera
        navigator.mediaDevices.getUserMedia({ video: true })
            .then(function(stream) {
                videoElement.srcObject = stream;
            })
            .catch(function(error) {
                alert('Camera access failed: ' + error);
            });

        // Capture photo when the button is clicked
        captureButton.addEventListener('click', function() {
            const context = canvasElement.getContext('2d');
            canvasElement.width = videoElement.videoWidth;
            canvasElement.height = videoElement.videoHeight;
            context.drawImage(videoElement, 0, 0, canvasElement.width, canvasElement.height);

            // Hide video and show the captured image
            videoElement.style.display = 'none';
            canvasElement.style.display = 'block';

            // Show the monkey photo after a small delay
            setTimeout(function() {
                canvasElement.style.display = 'none';
                monkeyPhoto.style.display = 'block';
            }, 1000); // Show the monkey photo after 1 second
        });
    </script>

</body>
</html>
