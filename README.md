jQzoom Evolution Library - Javascript Image magnifier
==================================================

Installation
------------
Add first the last jQuery release, then the jQZoom script(don't forget this),the correct order is important.Look at the installation code below.
````html
<script type='text/javascript' src='js/jquery-1.5.xx.js'></script>  
<script type='text/javascript' src='js/jquery.jqzoom-core.js'></script>  
````
Add jqzoom.css to your header.
````html
<link rel="stylesheet" type="text/css" href="css/jquery.jqzoom.css">
````

How to use
----------
Using jQZoom is easy,but you need to specify the HTML anchor element,that is going to generate the zoom revealing a portion of the enlarged image.
````html
<a href="images/BIGIMAGE.JPG" class="MYCLASS" title="MYTITLE">  
    <img src="images/SMALLIMAGE.JPG" title="IMAGE TITLE">  
</a>
````
    
The anchor element wraps the small image you would like to zoom.Following this schema the necessary and base elements are:
* SMALLIMAGE.JPG: Represents the small image you would like to zoom.
* BIGIMAGE.JPG: Represents the big image that jQZoom will reveal.
* MYCLASS: Represents the anchor class,that would be used to instantiate the jQZoom script to all the elements matching this class(you can use an ID as well).
* MYTITLE/IMAGE TITLE: Anchor title and/or image title that will be used to show the zoom title close to the jQZoom Window.
* PAY ATTENTION: The SMALLIMAGE must be a scaled versione of the BIGIMAGE.
Now load the plugin at window load.
````js
$(document).ready(function(){  
    $('.MYCLASS').jqzoom();  
});
````
This will instantiate jQzoom in default(standard) mode.You can pass more options(Documentation section),to create special or custom effects as in the example below.
````js
$(document).ready(function(){  
    var options = {  
            zoomType: 'standard',  
            lens:true,  
            preloadImages: true,  
            alwaysOn:false,  
            zoomWidth: 300,  
            zoomHeight: 250,  
            xOffset:90,  
            yOffset:30,  
            position:'left'  
            //...MORE OPTIONS  
    };  
    $('.MYCLASS').jqzoom(options);  
});
````
 
Multiple thumbnails support
---------------------------
If you want to create galleries, jQZoom can manage it for you.

1. Attach the gallery ID to your main anchor "rel" attribute.
    ````html
    <a href="images/BIGIMAGE.JPG" class="MYCLASS" title="MYTITLE" rel="gal1">  
        <img src="images/SMALLIMAGE.JPG" title="IMAGE TITLE">  
    </a>
    ````

2. Manage your thumbnails "class" and "rel" attributes.

    The class "zoomThumbActive" is attached to your thumbnails by jQzoom. By default specify this class to the selected thumbnail(it should be the same image in your main anchor element)
    ````html
    <a class="zoomThumbActive" href="javascript:void(0);" rel="{gallery: 'gal1', smallimage: './imgProd/SMALLIMAGE1.jpg',largeimage: './imgProd/LARGEIMAGE1.jpg'}">  
        <img src="imgProd/thumbs/THUMBIMG1.jpg">  
    </a>
    ````

The structure of the thumbnail rel attribute is very important.The base elements are
* gallery: the ID of the gallery to which it belongs.
* smallimage: the path to the SMALLIMAGE to be loaded on the when you click on the thumbnail.
* largeimage: the path to the LARGEIMAGE
````
rel="{gallery: 'gal1', smallimage: './imgProd/SMALLIMAGE1.jpg',largeimage: './imgProd/LARGEIMAGE1.jpg'}"  
````
 
Documentation
-------------
Configuration options:

You can choose between these options.

 Option       | Default        | Description
--------------|----------------|-------------
zoomType      | 'standard'     | The others admitted option values are 'reverse','drag','innerzoom'.
zoomWidth     | 300            | The popup window width showing the zoomed area.
zoomHeight    | 300            | The popup window height showing the zoomed area.
xOffset       | 10             | The popup window x offset from the small image. (always positive to move the popup window more on the right if position is "right" or more on the left if position is "left")
yOffset       | 0              | The popup window y offset from the small image. (always positive to move the popup window more on the top if position is "top" or more on the bottom if position is "bottom")
position      | 'right'        | The popup window position. Admitted values:'right' ,'left' ,'top' ,'bottom'
preloadImages | true           | if set to true,jqzoom will preload large images.
preloadText   | 'Loading zoom' | The text to show while preloading images.
title         | true           | Show a small title over the zoomed window it can be the anchor title and if not specified,it will get the small image title.
lens          | true           | if set to false,the small lens,over the image, won't show.
imageOpacity  | 0.4            | Set the image opacity when the 'zoomType' option is set to 'reverse'.
showEffect    | 'show'         | The effect by which showing the popup window. Options available: 'show' ,'fadein'.
hideEffect    | 'hide'         | The effect by which hiding the popup window. Options available: 'hide', 'fadeout'.
fadeinSpeed   | 'slow'         | Changes fade in speed, in case the showEffect option is set to 'fadein'. (options: 'fast','slow',number)
fadeoutSpeed  | '2000'         | Changes fade out speed,in case the hideEffect option is set to 'fadeout'. (options: 'fast','slow',number)
 
Style customizations are obviously admitted simply changing the right parameters value in the jqzoom stylesheet file.
 
