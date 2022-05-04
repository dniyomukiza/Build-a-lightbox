# Build-a-lightbox
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <link rel="stylesheet"href="lightbox.css">
    <script defer src= lightbox.js> </script>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LightBox</title>
</head>
<body>
    <div class="grid">
        <img src="http://source.unsplash.com/400x400?speakers">
        <img src="http://source.unsplash.com/400x400?microphones">
        <img src="http://source.unsplash.com/400x400?karaoke">
        <img src="http://source.unsplash.com/400x400?concert">
        <img src="http://source.unsplash.com/400x400?wedding">
        <img src="http://source.unsplash.com/400x400?inflatable">
        <img src="http://source.unsplash.com/400x400?champagne">
        <img src="http://source.unsplash.com/400x400?pool party">
        <img src="http://source.unsplash.com/400x400?celebration">
    </div>
</body>
</html>
===========================================================CSS=======================================================================

body{
    margin: 0;
}
.grid{
    display: grid;
    grid-template-columns: repeat(3,200px);
    justify-content: center;
    align-content: center;
    grid-gap:10px;
    height: 100vh;
}
.grid img{
    width: 200px;
    height: 200px;
    cursor: pointer;
}
#lightbox{
    position: fixed;
    z-index: 1000;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(0, 0, 0,.8);
    display: none;
}
#lightbox.active{
    display:flex;
    justify-content: center;
    align-items: center;
}
#lightbox img{
    max-width: 90%;
    max-height: 80%;
    padding: 5px;
    background-color: black;
    border: 2px solid white;
}
=======================================================JS=============================================

const lightbox=document.createElement('div')
lightbox.id='lightbox'
document.body.appendChild(lightbox)
const images= document.querySelectorAll('img')
images.forEach(image =>{
    image.addEventListener('click', e => {
        lightbox.classList.add('active')
        const img=document.createElement('img')
        img.src=image.src
        while(lightbox.firstChild){
            lightbox.removeChild(lightbox.firstChild)
        }
        lightbox.appendChild(img)


    })
})
lightbox.addEventListener('click', e => {
    if(e.target!==e.currentTarget)return
    lightbox.classList.remove('active')})
