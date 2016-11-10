---
title: "What Frame Windows Do"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: 7
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# What Frame Windows Do
Besides simply framing a view, frame windows are responsible for numerous tasks involved in coordinating the frame with its view and with the application. [CMDIFrameWnd](../VS_visualcpp/CMDIFrameWnd-Class.md) and [CMDIChildWnd](../VS_visualcpp/CMDIChildWnd-Class.md) inherit from [CFrameWnd](../VS_visualcpp/CFrameWnd-Class.md), so they have `CFrameWnd` capabilities as well as new capabilities that they add. Examples of child windows include views, controls such as buttons and list boxes, and control bars, including toolbars, status bars, and dialog bars.  
  
 The frame window is responsible for managing the layout of its child windows. In the MFC framework, a frame window positions any control bars, views, and other child windows inside its client area.  
  
 The frame window also forwards commands to its views and can respond to notification messages from control windows.  
  
## What do you want to know more about?  
  
-   [Control bars (how they fit into the frame window)](../VS_visualcpp/Control-Bars.md)  
  
-   [Managing menus, control bars, and accelerators (how they fit into the frame window)](../VS_visualcpp/Managing-Menus--Control-Bars--and-Accelerators.md)  
  
-   [Command Routing (from the frame window to its view and other command targets)](../VS_visualcpp/Command-Routing.md)  
  
-   [Document /View Architecture](../VS_visualcpp/Document-View-Architecture.md)  
  
-   [Control bars](../VS_visualcpp/Control-Bars.md)  
  
-   [Controls](../VS_visualcpp/Controls--MFC-.md)  
  
## See Also  
 [Frame Windows](../VS_visualcpp/Frame-Windows.md)