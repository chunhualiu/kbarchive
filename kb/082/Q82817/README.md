---
layout: page
title: "Q82817: Metafile (MS Draw) and Bitmap (Paintbrush) Pictures"
permalink: /kb/082/Q82817/
---

## Q82817: Metafile (MS Draw) and Bitmap (Paintbrush) Pictures

{% raw %}

	Article: Q82817
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-SEP-1999
	
	3.10 3.11
	WINDOWS
	kbtool kbole
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Two basic types of pictures are supported by applications for Microsoft Windows.
	One is the Windows metafile (*.WMF), and the other is the bitmap (*.BMP and
	others). The basic difference between these types lies in how they represent the
	picture.
	
	A bitmap is an expanse of dots, called pixels or pels. Every pixel is the same
	size, but may be one of a series of colors. Shapes drawn in a bitmap may be
	limited by this pixel format. For example, a solid circle drawn in a bitmap is
	really just a rough approximation of a circle, with pixels inside the circle
	being set to a different color than those pixels outside the circle. The bitmap
	can be stretched or shrunk, but doing so usually creates undesirable effects,
	such as rough edges and odd patterns in the picture.
	
	Bitmaps are useful for very detailed images, such as computer screens and
	digitized photographs. This format is often called a "raster" graphic. Bitmaps
	can be created with bitmap editors, such as Paintbrush (included in Microsoft
	Windows versions 3.0 and 3.1). Bitmaps usually have the MS-DOS file extension of
	.BMP, but third parties have other formats for their bitmaps, notably Z-Soft
	Corporation's .PCX format. Generally, Windows works best with the Windows bitmap
	format (.BMP).
	
	A metafile, unlike a bitmap, is a series of shapes and colors that are drawn in a
	prescribed order on the screen or printer. A circle in a metafile, for example,
	will remain a circle and can be stretched without showing the rough patterns
	seen in bitmaps. The drawing process for metafiles is similar to a recording of
	the image's original creation, where each shape is quickly drawn in the same
	order in which it was originally created. This is often called a "vector"
	graphic. Metafiles can be created with metafile editors, such as MS Draw
	(included with Microsoft Word for Windows version 2.0). Metafiles usually have
	the MS-DOS file extension of .WMF.
	
	The OLE feature can embed or link either bitmap or metafile images. When a
	metafile image is embedded or linked, the server application (the application
	associated with the object) for such objects will be a metafile editor such as
	MS Draw. Bitmaps that are embedded or linked use the Paintbrush picture to
	represent the server application.
	
	Additional query words: 3.10 3.1
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
