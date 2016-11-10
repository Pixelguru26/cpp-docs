---
title: "towctrans"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - towctrans
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
  - api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
caps.latest.revision: 10
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
# towctrans
Transforms a character.  
  
## Syntax  
  
```  
wint_t towctrans(  
   wint_t c,  
   wctrans_t category   
);  
```  
  
#### Parameters  
 `c`  
 The character you want to transform.  
  
 `category`  
 An identifier that contains the return value of [wctrans](../VS_visualcpp/wctrans.md).  
  
## Return Value  
 The character `c`, after `towctrans` used the transform rule in `category`.  
  
## Remarks  
 The value of `category` must have been returned by an earlier successful call to [wctrans](../VS_visualcpp/wctrans.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`towctrans`|<wctype.h>|  
  
 For additional compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md) in the Introduction.  
  
## Example  
 See `wctrans` for a sample that uses `towctrans`.  
  
## See Also  
 [Data Conversion](../VS_visualcpp/Data-Conversion.md)