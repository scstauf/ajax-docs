---
title: Appearance Skins
page_title: Appearance Skins | UI for ASP.NET AJAX Documentation
description: Appearance Skins
slug: menu/appearance-and-styling/appearance-skins
tags: appearance,skins
published: True
position: 5
---

# Appearance Skins



Each of the controls included in the RadControls for ASP.NET AJAX suite is styled with __two css files__that are loaded in certain order. The first one - ControlName.css, also called __base stylesheet__ contains CSS properties and values that are commonfor all skins, i.e it is layout-specific, not skin-specific. These are CSS float, padding, margin, font-size, font-family, etc.In the general case, when creating a custom skin for a control this file should not be edited, unless the custom skin needs different sizes, paddings or margins. The second file represents the actual skin of the control, and its name consists of the control name plus the skin name,i.e - Menu.Default.css. Upon creating a custom skin for the control, one should edit that particular file, as it contains skin-specificCSS properties, and references to images, colors, borders and backgrounds.

__RadMenu__ uses __skins__ to control the overall look-and-feel of the menu. A skin is a set of images and a CSS stylesheet that can be applied to the menu elements (items, images, etc.) and defines their look and feel. To apply a skin to the menu, set its __Skin__ property, either using the properties pane or the __RadMenu__[Smart Tag]({%slug menu/design-time/smart-tag%}).

__RadMenu__ is installed with a number of built-in skins:![RadMenu Skins](images/menu_skinsthumb.png)

>note The __Hay__ , __Forest__ , __Sitefinity__ and __Transparent__ skins are obsolete and have been removed from the Telerik.Web.UI.Skins.dll assembly as of __Q1 2014__ .You can find more information on the matter in[this blog post](http://blogs.telerik.com/aspnet-ajax/posts/13-04-11/6-telerik-asp.net-ajax-skins-going-obsolete).
>




## Customizing Skins

You can tweak the existing skins, or create your own. Each skin has two main elements: images and a stylesheet. When creating your own, it is a good idea to start with the stylesheet for an existing skin and alter that. See [Tutorial: Creating a Custom Skin]({%slug menu/appearance-and-styling/tutorial:-creating-a-custom-skin%}) for a step-by-step walk through. To use your own skin

1. Add the new CSS file to your project.

1. Drag and drop the CSS file from the Project Explorer onto your Web page.

1. Set the __EnableEmbeddedSkins__ property of the __RadMenu__ to __False__.

The stylesheet for a __RadMenu__ skin has the name __Menu.[SkinName].css__ and can be found in the __...Skins/[SkinName]__ directory. The images are found in the __...Skins/[SkinName]/Menu__ directory. For example, the stylesheet for the "Black" skin is called Menu.Black.css and is located in the ...Skins/Menu directory. The images are found in the ...Skins/Black/Menu directory. The images are referenced by name from within the stylesheet.

For more information on the CSS File structure, see the [Understanding the Skin CSS File]({%slug menu/appearance-and-styling/understanding-the-skin-css-file%}) topic.

# See Also

 * [Setting  the CSS Class of Items]({%slug menu/appearance-and-styling/setting--the-css-class-of-items%})

 * [Adding Images to Items]({%slug menu/appearance-and-styling/adding-images-to-items%})

 * [Layout of Root Items ]({%slug menu/appearance-and-styling/layout-of-root-items-%})