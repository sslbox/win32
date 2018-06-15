---
Description: The window background is the color or pattern used to fill the client area before a window begins drawing.
ms.assetid: 72a342dc-2766-4ec9-b4c6-5ac3c550ea25
title: Window Background
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Window Background

The window background is the color or pattern used to fill the client area before a window begins drawing. The window background covers whatever was on the screen before the window was moved there, erasing existing images and preventing the application's new output from being mixed with unrelated information.

The system paints the background for a window or gives the window the opportunity to do so by sending it a [**WM\_ERASEBKGND**](https://www.bing.com/search?q=**WM\_ERASEBKGND**) message when the application calls [**BeginPaint**](/windows/desktop/api/Winuser/nf-winuser-beginpaint). If an application does not process the message but passes it to [**DefWindowProc**](https://www.bing.com/search?q=**DefWindowProc**), the system erases the background by filling it with the pattern in the background brush specified by the window's class. If the brush is not valid or the class has no background brush, the system sets the **fErase** member in the [**PAINTSTRUCT**](/windows/desktop/api/Winuser/ns-winuser-tagpaintstruct) structure that **BeginPaint** returns, but carries out no other action. The application then has a second chance to draw the window background, if necessary.

If it processes [**WM\_ERASEBKGND**](https://www.bing.com/search?q=**WM\_ERASEBKGND**), the application should use the message's *wParam* parameter to draw the background. This parameter contains a handle to the display device context for the window. After drawing the background, the application should return a nonzero value. This ensures that [**BeginPaint**](/windows/desktop/api/Winuser/nf-winuser-beginpaint) does not erroneously set the **fErase** member of the [**PAINTSTRUCT**](/windows/desktop/api/Winuser/ns-winuser-tagpaintstruct) structure to a nonzero value (indicating the background should be erased) when the application processes the subsequent [**WM\_PAINT**](wm-paint.md) message.

An application can define a class background brush by assigning a brush handle or a system color value to the **hbrBackground** member of the [**WNDCLASS**](https://www.bing.com/search?q=**WNDCLASS**) structure when registering the class with the [**RegisterClass**](https://www.bing.com/search?q=**RegisterClass**) function. The [**GetStockObject**](/windows/desktop/api/Wingdi/nf-wingdi-getstockobject) or [**CreateSolidBrush**](/windows/desktop/api/Wingdi/nf-wingdi-createsolidbrush) function can be used to create a brush handle. A system color value can be one of those defined for the [**SetSysColors**](https://www.bing.com/search?q=**SetSysColors**) function. (The value must be increased by one before it is assigned to the member.)

An application can process the [**WM\_ERASEBKGND**](https://www.bing.com/search?q=**WM\_ERASEBKGND**) message even though a class background brush is defined. This is typical in applications that enable the user to change the window background color or pattern for a specified window without affecting other windows in the class. In such cases, the application must not pass the message to [**DefWindowProc**](https://www.bing.com/search?q=**DefWindowProc**).

It is not necessary for an application to align brushes, because the system draws the brush using the window origin as the point of reference. Given this, the user can move the window without affecting the alignment of pattern brushes.

 

 


