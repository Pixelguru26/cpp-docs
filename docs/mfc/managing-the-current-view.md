---
title: "Managing the Current View"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "views, and OnActivateView method"
  - "views, deactivating"
  - "views, activating"
  - "frame windows, current view"
  - "OnActivateView method"
  - "views, current"
  - "deactivating views"
  - "current view in frame window"
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: 7
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Managing the Current View
As part of the default implementation of frame windows, a frame window keeps track of a currently active view. If the frame window contains more than one view, as for example in a splitter window, the current view is the most recent view in use. The active view is independent of the active window in Windows or the current input focus.  
  
 When the active view changes, the framework notifies the current view by calling its [OnActivateView](../Topic/CView::OnActivateView.md) member function. You can tell whether the view is being activated or deactivated by examining `OnActivateView`'s `bActivate` parameter. By default, `OnActivateView` sets the focus to the current view on activation. You can override `OnActivateView` to perform any special processing when the view is deactivated or reactivated. For example, you might want to provide special visual cues to distinguish the active view from other, inactive views.  
  
 A frame window forwards commands to its current (active) view, as described in [Command Routing](../mfc/command-routing.md), as part of the standard command routing.  
  
## See Also  
 [Using Frame Windows](../mfc/using-frame-windows.md)