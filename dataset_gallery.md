---
layout: default
title: Interactive Dataset Gallery
---

[Homepage](./)

<nav id="breadcrumb"></nav> <!-- Breadcrumb navigation -->

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
    #breadcrumb {
        margin-bottom: 20px;
    }
    .breadcrumb-item {
        margin-right: 5px;
        cursor: pointer;
    }
</style>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        loadDirectory(['root']); // Load root directory initially as an array
    });

    function loadDirectory(pathArray) {
        const galleryRoot = document.getElementById('gallery-root');
        const breadcrumb = document.getElementById('breadcrumb');
        galleryRoot.innerHTML = '';
        breadcrumb.innerHTML = '<span class="breadcrumb-item" onclick="loadDirectory([\'root\'])">Root</span>';

        // Update breadcrumb
        let pathSoFar = ['root'];
        for (let i = 1; i < pathArray.length; i++) {
            let part = pathArray[i];
            pathSoFar.push(part);
            breadcrumb.innerHTML += ' / <span class="breadcrumb-item" onclick="loadDirectory([\'' + pathSoFar.join('\',\'') + '\'])">' + part.charAt(0).toUpperCase() + part.slice(1).split('.').join(' > ') + '</span>';
        }

        // Directory-specific content
        const directoryPath = pathArray[pathArray.length - 1];
        if (directoryPath === 'root') {
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\',\'Natural\'])">Natural</div>';
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\',\'subdir2\'])">Manufactured</div>';
        } else if (directoryPath === 'Natural') {
            galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\',\'Natural\',\'Sagui\'])">Sagui</div>';            
            //galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\'])">Back to Root</div>';
        } else if (directoryPath === 'Sagui') {
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/thumbnail?id=1uTwbW5jrwS7s80ChtzwjefIILOC_T15P" alt="Image 1">';
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_2" alt="Image 2">';
            //galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\', \'Natural\'])">Back to "Natural"</div>';
        } else if (directoryPath === 'subdir2') {
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_3" alt="Image 3">';
            galleryRoot.innerHTML += '<img class="gallery-image" src="https://drive.google.com/uc?export=view&id=YOUR_IMAGE_ID_4" alt="Image 4">';
            //galleryRoot.innerHTML += '<div class="directory-link" onclick="loadDirectory([\'root\'])">Back to Root</div>';
        }
        // Add more conditions for other subdirectories
    }
</script>
