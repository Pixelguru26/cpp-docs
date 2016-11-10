---
title: "feraiseexcept"
ms.custom: na
ms.date: 10/06/2016
ms.devlang: 
  - C
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - cpp
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - feraiseexcept
apilocation: 
  - msvcrt.dll
  - msvcr80.dll
  - msvcr90.dll
  - msvcr100.dll
  - msvcr100_clr0400.dll
  - msvcr110.dll
  - msvcr110_clr0400.dll
  - msvcr120.dll
  - msvcr120_clr0400.dll
  - ucrtbase.dll
apitype: HeaderDef
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
manager: ghogen
translation.priority.mt: 
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
# feraiseexcept
Raises the specified floating-point exceptions.  
  
## Syntax  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### Parameters  
 `excepts`  
 The floating-point exceptions to raise.  
  
## Return Value  
 If all specified exceptions are raised successfully, returns 0.  
  
## Remarks  
 The `feraiseexcept` function attempts to raise the floating-point exceptions specified by `excepts`.   The `feraiseexcept` function supports these exception macros, defined in <fenv.h>:  
  
|Exception Macro|Description|  
|---------------------|-----------------|  
|FE_DIVBYZERO|A singularity or pole error occurred in an earlier floating-point operation; an infinity value was created.|  
|FE_INEXACT|The function was forced to round the stored result of an earlier floating-point operation.|  
|FE_INVALID|A domain error occurred in an earlier floating-point operation.|  
|FE_OVERFLOW|A range error occurred; an earlier floating-point operation result was too large to be represented.|  
|FE_UNDERFLOW|An earlier floating-point operation result was too small to be represented at full precision; a denormal value was created.|  
|FE_ALLEXCEPT|The bitwise OR of all supported floating-point exceptions.|  
  
 The `excepts` argument may be zero, one of the exception macro values, or the bitwise OR of two or more of the supported exception macros. If one of the specified exception macros is FE_OVERFLOW or FE_UNDERFLOW, the FE_INEXACT exception may be raised as a side-effect.  
  
 To use this function, you must turn off floating-point optimizations that could prevent access by using the `#pragma fenv_access(on)` directive prior to the call. For more information, see [fenv_access](../VS_visualcpp/fenv_access.md).  
  
 **Microsoft Specific:** The exceptions specified in `excepts` are raised in the order FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. However, FE_INEXACT can be raised when FE_OVERFLOW or FE_UNDERFLOW is raised, even if not specified in `excepts`. **End Microsoft Specific**  
  
## Requirements  
  
|Function|C header|C++ header|  
|--------------|--------------|------------------|  
|`feraiseexcept`|<fenv.h>|<cfenv\>|  
  
 For additional compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md).  
  
## See Also  
 [Alphabetical Function Reference](../VS_visualcpp/CRT-Alphabetical-Function-Reference.md)   
 [fesetexceptflag](../VS_visualcpp/fesetexceptflag2.md)   
 [feholdexcept](../VS_visualcpp/feholdexcept2.md)   
 [fetestexcept](../VS_visualcpp/fetestexcept1.md)   
 [feupdateenv](../VS_visualcpp/feupdateenv.md)