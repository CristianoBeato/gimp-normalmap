# GIMP normalmap plugin #

## Contents ##
  * [Overview](#Overview.md)
  * [Features](#Features.md)
  * [Download](#Download.md)
  * [Changes](#Changes.md)
  * [Screenshots](#Screenshots.md)

## Overview ##
This is a plugin for GIMP version 2.8.x. It allows you to convert images into RGB normal maps for use in per-pixel lighting applications. The goal is to completely clone NVIDIA's photoshop plugin, with a few new useful features.

## Features ##
  * Filters. These include the filters found in the NVIDIA plugin (4 sample, 3x3, 5x5, 7x7 and 9x9) with the addition of 3x3 and 5x5 Sobel and Prewitt edge detection filters (yields the best results IMO).
  * Post-filtering normal scaling
  * Wrap mode. This allows the filters to wrap around the image. Useful for creating normalmaps from a tiling bumpmap.
  * Height source. Use an average of the RGB components or the alpha channel as the height source in the generation of the normals.
  * Alpha result. For RGBA images, the alpha channel can either remain unchanged, have the height used to generate the normal written to it, inverse height, be replaced by either 0 or 1, the inverse of the alpha channel's current value or use the value of a grayscale image.
  * Conversion options including "Normalize only" for renormalizing bumpmaps.
  * "Convert to height" conversion option to reclaim height maps from normal maps (use in tandem with the Invert X and Invert Y options).
  * DU/DV map creation (8 and 16 bit, signed or unsigned)
  * Dynamic 2D preview in the interactive dialog.
  * Dynamic 3D preview window using OpenGL to view the normal map applied to a lit 3D mesh. Here are some of it's features:
    * View normal map applied to a number of 3D meshes (quad, cube, sphere, torus and teapot)
    * Shading is done with a number of bump mapping techniques (dot3, parallax, parallax occlusion and relief mapping) using the OpenGL Shading Language (GLSL)
    * Full scene navigation controls (Rotate the object, light or scene)
    * Fullscreen viewing support
    * Specular lighting toggle with exponent slider
    * Ability to choose ambient, diffuse and specular light colors
    * UV coordinate scaling

## Download ##
Downloads are provided either in source code form, or pre-built Windows 32-bit binaries.  You can find them on the left side bar, or under the Downloads tab.
To compile the source, refer to the INSTALL file provided in the source package and make sure you have everything you need installed. The GNU Makefiles should work on every system that has GNU make installed. Sorry, no MSVC project/nmake files included. I don't own it, so you are on your own.

## Changes ##
**1.2.3** (2012-06-23) [SVN](http://code.google.com/p/gimp-normalmap/source/browse/#svn/tags/release-1.2.3)
  * Various bug fixes
  * GIMP 2.8 support
  * Native Windows 64-bit binaries

**1.2.2**
  * No changes, recompiled against GIMP 2.6
  * Updated readme file for windows binaries

**1.2.1**
  * Added "DUDV to Normal" conversion option.
  * Removed requirement for the GL\_SGIS\_generate\_mipmap extension.
  * Various bug fixes.

**1.2**
  * Added Invert X, Invert Y and Swap RGB options
  * Moved "Wrap" to the new Options panel
  * Added "Convert to height" conversion option. This allows you to reclaim a height map from a normal map. Use in tandem with the Invert X and Invert Y options to get it to look right. Also, there is a "Contrast" setting that is enabled when choosing this conversion option to allow you to tweak the height map further. The algorithm isn't perfect, but it's a start.
  * New overhauled and possibly overkill 3D preview window. Too many new features to list here. See for yourself. :)

**1.0.2**
  * Added 5x5 Sobel and Prewitt edge detection filters
  * Switched to GLEW for OpenGL extension loading/checking
  * Added Windows build support with a MinGW environment

**1.0.1**
  * Fixed RGB Bias conversion option
  * Fixed a possible crash with the GTK+ dialog

**1.0**
  * Added support for GIMP 2.0.x, removed support for 1.2.x and 1.3.x.
  * Added alpha channel source "Alpha map" which allows you to encode a grayscale image into the alpha channel of the normal map

**0.5**
  * Higher quality 2D and 3D preview
  * Double sided lighting in 3D preview
  * More UI cleanups

**0.4**
  * Added DU/DV map creation options
  * More UI issues addressed

**0.3**
  * Fixed the "Normalize only" conversion method
  * Various UI issues fixed

**0.2**
  * Added 3D preview window for both versions
  * Added the Prewitt edge detection filter
  * Fixed bug that caused the dv portion of the filter kernels to be inverted

## Screenshots ##
<table border='0' cellspacing='15'>
<blockquote><tr align='center'>
<blockquote><td valign='top'>
<b>Release 1.2 running in GIMP 2.3.4</b><br /><br />
<img src='http://gimp-normalmap.googlecode.com/svn/wiki/images/shot01.jpg' />
</td>
<td valign='top'>
<b>New 3D preview window</b><br /><br />
<img src='http://gimp-normalmap.googlecode.com/svn/wiki/images/shot02.jpg' />
</td>
</blockquote></tr>
<tr align='center'>
<blockquote><td valign='top'>
<b>New "Convert to height" conversion option in 1.2</b><br /><br />
<img src='http://gimp-normalmap.googlecode.com/svn/wiki/images/shot03.jpg' />
</td>
</blockquote></tr>
</table>