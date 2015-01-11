---
layout: post
category : Articles
tagline: 
tags : [Drupal, webdev, CSS, JavaScript, MySQL]
---
{% include JB/setup %}

### Overview

Before I pull the plug on my long running [baconology](http://baconology.org/ "Baconology") site, I want to hide
the annoying watermarks to incoming visitors. In order to achieve this, I will use CSS to hide a portion of the image.

___

![post_watermark](/assets/img/baconology/watermark-example.png)

___

![recipe_watermark](/assets/img/baconology/watermark-example-recipe.png)

___

The watermark height is constant, 

### Set the HTML input filter

This may be overkill since we're touching the content post-rendering but it doesn't hurt to set the filtering to full HTML
since I'm the only one prodiving the content anyway.

    UPDATE node_revisions
        SET format = 2;

Format 2 means 'Full HTML', I got this from poking around with the form value and watching the changed happening inside
the database as I was changed those values.

### CSS rules

Lets define a few CSS rules that will take care of hiding the bottom portion of the image

    .watermark-container {
      max-width: 700px;
      overflow: hidden; 
    }
    
    img.watermark-bottom {
      width: 100%;
      height: auto;
      margin-bottom: -30px;
    }
        
    img.watermark-bottom-teaser {
      width: 100%;
      height: auto;
      margin-bottom: -30px;
    }
    
    img.watermark-bottom-recipe {
      width : 300px
      height: auto;
      margin-bottom: -30px;
    }
    
The magic happens when the wrapping div hide the overflow from the nested element that has a negative margin.

I could have used the same rule for all watermarked image classes but I prefer to be able to tweak them individually later
on.

### Javascript

A simple JQuery function will select all the relevant images and wrap them in a proper div element

    $(function() {
        $('img.watermark-bottom, img.watermark-bottom-recipe, img.watermark-bottom-teaser' ).wrap( "<div class='watermark-container'></div>" );
    });

###Update the content

It takes way too long to edit each individual articles. We'll be adding an html class
programatically using the MySQL replace functionality.

First, lets update node revisions for the individual blog posts

    UPDATE node_revisions
        SET body = REPLACE(body,'<img ','<img class="watermark-bottom" ');

Then the teasers need to be updated as well

    UPDATE node_revisions
        SET teaser = REPLACE(teaser,'<img ','<img class="watermark-bottom-teaser" ');

I also have another content type 'recipe' that needs the same type of CSS rules

    UPDATE content_type_recipe
        SET field_recipeimage_value = REPLACE(field_recipeimage_value,'<img ','<img class="watermark-bottom-recipe" ');
    
### Result

Watermark hidden from blog posts

___

![post_watermark](/assets/img/baconology/no-watermark-example.png)


Watermark hidden from recipes

___

![recipe_watermark](/assets/img/baconology/no-watermark-example-recipe.png)

People who link to the site will still see the watermark, people who visit the site directly will not be bothered by it.