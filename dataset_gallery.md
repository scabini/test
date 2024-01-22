---
layout: default
title: Interactive Dataset Gallery
---

[Homepage](./)

<div id="gallery-root">
    <!-- Gallery content will be dynamically loaded here -->
</div>

<style>
    #gallery-root {
        display: flex;
        flex-wrap: wrap;
        padding: 10px;
    }
    .gallery-image {
        margin: 5px;
        border: 2px solid #ccc;
        max-width: 200px;
        height: auto;
    }
    .directory-link {
        margin: 10px;
        cursor: pointer;
        color: blue;
    }
</style>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        loadDirectory('root'); // Load root directory initially
    });

    function loadDirectory(directoryPath) {
        const galleryRoot = document.getElementById('gallery-root');
        galleryRoot.innerHTML = '';

        if (directoryPath === 'root') {
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'subdir1\')">Natural</div>';
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'subdir2\')">Manufactured</div>';
            
        } else if (directoryPath === 'subdir1') {
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'subdir1.1\')">Sagui</div>';            
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'root\')">Back to Root</div>';

        } else if (directoryPath === 'subdir1.1') {
            
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/thumbnail?id=1uTwbW5jrwS7s80ChtzwjefIILOC_T15P" alt="Image 1">';
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_2" alt="Image 2">';
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'subdir1\')">Back to "Natural"</div>';
            
        } else if (directoryPath === 'subdir2') {
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_3" alt="Image 3">';
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_4" alt="Image 4">';
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory(\'root\')">Back to Root</div>';
        }
        // Add more conditions for other subdirectories
    }
</script>
