---
title: "CSimpleMapEqualHelperFalse Class"
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
ms.topic: reference
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 13
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
# CSimpleMapEqualHelperFalse Class
This class is a helper for the [CSimpleMap](../VS_visualcpp/CSimpleMap-Class.md) class.  
  
## Syntax  
  
```  
template < class TKey, class TVal > class CSimpleMapEqualHelperFalse  
```  
  
## Members  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](../Topic/CSimpleMapEqualHelperFalse::IsEqualKey.md)|(Static) Tests two keys for equality.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](../Topic/CSimpleMapEqualHelperFalse::IsEqualValue.md)|(Static) Returns false.|  
  
## Remarks  
 This traits class is a supplement to the `CSimpleMap` class. It provides a method for comparing two elements contained in the `CSimpleMap` object, specifically two value elements or two key elements.  
  
 The value comparison will always return false, and in addition, will call `ATLASSERT` with an argument of false if it is ever referenced. In situations where the equality test is not sufficiently defined, this class allows a map containing key/value pairs to operate correctly for most methods but fail in a well-defined manner for methods that depend on comparisons such as [CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md).  
  
## Requirements  
 **Header:** atlsimpcoll.h  
  
##  <a name="csimplemapequalhelperfalse__isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey  
 Tests two keys for equality.  
  
```  
static bool IsEqualKey(  
    const TKey& k1,  
    const TKey& k2 );  
```  
  
### Parameters  
 `k1`  
 The first key.  
  
 `k2`  
 The second key.  
  
### Return Value  
 Returns true if the keys are equal, false otherwise.  
  
### Remarks  
 This method calls [CSimpleArrayEqualHelper](../VS_visualcpp/CSimpleArrayEqualHelper-Class.md).  
  
##  <a name="csimplemapequalhelperfalse__isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue  
 Returns false.  
  
```  
static bool IsEqualValue(  
    const TVal&,  
    const TVal&   
   );  
```  
  
### Return Value  
 Returns false.  
  
### Remarks  
 This method always returns false, and will call `ATLASSERT` with an argument of false if it is ever referenced. The purpose of `CSimpleMapEqualHelperFalse::IsEqualValue` is to force methods using comparisons to fail in a well-defined manner when equality tests have not been adequately defined.  
  
## See Also  
 [CSimpleMapEqualHelper Class](../VS_visualcpp/CSimpleMapEqualHelper-Class.md)   
 [Class Overview](../VS_visualcpp/ATL-Class-Overview.md)