---
title: "NMAKE Fatal Error U1099"
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
ms.topic: error-reference
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
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
# NMAKE Fatal Error U1099
stack overflow  
  
 The makefile being processed was too complex for the current stack allocation in NMAKE. NMAKE has an allocation of 0x3000 (12K).  
  
 To increase NMAKE's stack allocation, run the [editbin /stack](../VS_visualcpp/-STACK.md) utility with a larger stack option:  
  
 **editbin /STACK:reserve NMAKE.EXE**  
  
 where *reserve* is a number greater than the current stack allocation in NMAKE.