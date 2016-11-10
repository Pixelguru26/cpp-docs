---
title: "num_put Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "std::num_put"
  - "xlocnum/std::num_put"
  - "num_put"
  - "std.num_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_put class"
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: 18
ms.author: "corob"
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
# num_put Class
A template class that describes an object that can serve as a locale facet to control conversions of numeric values to sequences of type `CharType`.  
  
## Syntax  
  
```
template<class CharType, class OutputIterator = ostreambuf_iterator<CharType>
> class num_put : public locale::facet;
```  
  
#### Parameters  
 `CharType`  
 The type used within a program to encode characters in a locale.  
  
 `OutputIterator`  
 The type of iterator to which the numeric put functions write their output.  
  
## Remarks  
 As with any locale facet, the static object ID has an initial stored value of zero. The first attempt to access its stored value stores a unique positive value in **id.**  
  
### Constructors  
  
|||  
|-|-|  
|[num_put](#num_put__num_put)|The constructor for objects of type `num_put`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char_type](#num_put__char_type)|A type that is used to describe a character used by a locale.|  
|[iter_type](#num_put__iter_type)|A type that describes an output iterator.|  
  
### Member Functions  
  
|||  
|-|-|  
|[do_put](#num_put__do_put)|A virtual function that is called to convert a number into a sequence of `CharType`s that represents the number formatted for a given locale.|  
|[put](#num_put__put)|Converts a number into a sequence of `CharType`s which represents the number formatted for a given locale.|  
  
## Requirements  
 **Header:** \<locale>  
  
 **Namespace:** std  
  
##  <a name="num_put__char_type"></a>  num_put::char_type  
 A type that is used to describe a character used by a locale.  
  
```
typedef CharType char_type;
```  
  
### Remarks  
 The type is a synonym for the template parameter **CharType**.  
  
##  <a name="num_put__do_put"></a>  num_put::do_put  
 A virtual function that is called to convert a number into a sequence of **CharType**s that represents the number formatted for a given locale.  
  
```
virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```  
  
### Parameters  
 `next`  
 An iterator addressing the first element of the inserted string.  
  
 `_Iosbase`  
 Specified the stream which contains locale with the numpunct facet used to punctuate the output and flags for formatting the output.  
  
 `_Fill`  
 A character that is used for spacing.  
  
 `val`  
 The number or Boolean type that is to be output.  
  
### Return Value  
 An output iterator the addresses the position one beyond the last element produced.  
  
### Remarks  
 The first virtual protected member function generates sequential elements beginning at `next` to produce an integer output field from the value of `val`. The function returns an iterator designating the next place to insert an element beyond the generated integer output field.  
  
 The integer output field is generated by the same rules used by the print functions for generating a series of `char` elements to a file. Each such char element is assumed to map to an equivalent element of type **CharType** by a simple, one-to-one mapping. Where a print function pads a field with either spaces or the digit 0, however, `do_put` instead uses **fill**. The equivalent print conversion specification is determined as follows:  
  
-   If **iosbase**. [flags](../stdcpplib/ios_base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../stdcpplib/-ios--functions.md#oct), the conversion specification is **lo**.  
  
-   If **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../stdcpplib/-ios--functions.md#hex), the conversion specification is **lx**.  
  
-   Otherwise, the conversion specification is **ld**.  
  
 If **iosbase**. [width](../stdcpplib/ios_base-class.md#ios_base__width) is nonzero, a field width of this value is prepended. The function then calls **iosbase**. **width**(0) to reset the field width to zero.  
  
 Padding occurs only if the minimum number of elements *N* required to specify the output field is less than **iosbase**. [width](../stdcpplib/ios_base-class.md#ios_base__width). Such padding consists of a sequence of *N* – **width** copies of **fill**. Padding then occurs as follows:  
  
-   If **iosbase**. **flags** & `ios_base::adjustfield` == `ios_base::`[left](../stdcpplib/-ios--functions.md#left), the flag **–** is prepended. (Padding occurs after the generated text.)  
  
-   If **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../stdcpplib/-ios--functions.md#internal), the flag **0** is prepended. (For a numeric output field, padding occurs where the print functions pad with 0.)  
  
-   Otherwise, no additional flag is prepended. (Padding occurs before the generated sequence.)  
  
 Finally:  
  
-   If **iosbase**. **flags** & `ios_base::`[showpos](../stdcpplib/-ios--functions.md#showpos) is nonzero, the flag **+** is prepended to the conversion specification.  
  
-   If **iosbase**. **flags** & **ios_base::**[showbase](../stdcpplib/-ios--functions.md#showbase) is nonzero, the flag **#** is prepended to the conversion specification.  
  
 The format of an integer output field is further determined by the [locale facet](../stdcpplib/locale-class.md#facet_class)**fac** returned by the call [use_facet](../stdcpplib/-locale--functions.md#use_facet) < [numpunct](../stdcpplib/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../stdcpplib/ios_base-class.md#ios_base__getloc)). Specifically:  
  
- **fac**. [grouping](../stdcpplib/numpunct-class.md#numpunct__grouping) determines how digits are grouped to the left of any decimal point  
  
- **fac**. [thousands_sep](../stdcpplib/numpunct-class.md#numpunct__thousands_sep) determines the sequence that separates groups of digits to the left of any decimal point  
  
 If no grouping constraints are imposed by **fac**. **grouping** (its first element has the value CHAR_MAX), then no instances of **fac**. `thousands_sep` are generated in the output field. Otherwise, separators are inserted after the print conversion occurs.  
  
 The second virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```  
  
 behaves the same as the first, except that it replaces a conversion specification of **ld** with **lu**.  
  
 The third virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```  
  
 behaves the same as the first, except that it produces a floating-point output field from the value of **val**. **fac**. [decimal_point](../stdcpplib/numpunct-class.md#numpunct__decimal_point) determines the sequence that separates the integer digits from the fraction digits. The equivalent print conversion specification is determined as follows:  
  
-   If **iosbase**. **flags** & `ios_base::floatfield` == `ios_base::`[fixed](../stdcpplib/-ios--functions.md#fixed), the conversion specification is **lf**.  
  
-   If **iosbase**. **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../stdcpplib/-ios--functions.md#scientific), the conversion specification is `le`. If **iosbase**. **flags** & `ios_base::`[uppercase](../stdcpplib/-ios--functions.md#uppercase) is nonzero, **e** is replaced with **E**.  
  
-   Otherwise, the conversion specification is **lg**. If **iosbase**. **flags** & **ios_base::uppercase** is nonzero, **g** is replaced with **G**.  
  
 If **iosbase**. **flags** & **ios_base::fixed** is nonzero or if **iosbase**. [precision](../stdcpplib/ios_base-class.md#ios_base__precision) is greater than zero, a precision with the value **iosbase**. **precision** is prepended to the conversion specification. Any padding behaves the same as for an integer output field. The padding character is **fill**. Finally:  
  
-   If **iosbase**. **flags** & `ios_base::`[showpos](../stdcpplib/-ios--functions.md#showpos) is nonzero, the flag **+** is prepended to the conversion specification.  
  
-   If **iosbase**. **flags** & `ios_base::`[showpoint](../stdcpplib/-ios--functions.md#showpoint) is nonzero, the flag **#** is prepended to the conversion specification.  
  
 The fourth virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```  
  
 behaves the same the third, except that the qualifier **l** in the conversion specification is replaced with **L**.  
  
 The fifth virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void *val) const;
```  
  
 behaves the same the first, except that the conversion specification is `p`**,** plus any qualifier needed to specify padding.  
  
 The sixth virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```  
  
 behaves the same as the first, except that it generates a Boolean output field from `val`.  
  
 A Boolean output field takes one of two forms. If **iosbase**. **flags** & `ios_base::`[boolalpha](../stdcpplib/-ios--functions.md#boolalpha) is **false**, the member function returns `do_put`(_ *Next*, \_ *Iosbase*, \_ *Fill*, ( **long**) `val`), which typically produces a generated sequence of either 0 (for **false**) or 1 (for **true**). Otherwise, the generated sequence is either **fac**. [falsename](../stdcpplib/numpunct-class.md#numpunct__falsename)`)` (for **false**), or **fac**. [truename](../stdcpplib/numpunct-class.md#numpunct__truename) (for **true**).  
  
 The seventh virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```  
  
 behaves the same as the first, except that it replaces a conversion specification of **ld** with **lld**.  
  
 The eighth virtual protected member function:  
  
```
virtual iter_type         do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```  
  
 behaves the same as the first, except that it replaces a conversion specification of `ld` with `llu`.  
  
### Example  
  See the example for [put](#num_put__put), which calls `do_put`.  
  
##  <a name="num_put__iter_type"></a>  num_put::iter_type  
 A type that describes an output iterator.  
  
```
typedef OutputIterator iter_type;
```  
  
### Remarks  
 The type is a synonym for the template parameter **OutputIterator.**  
  
##  <a name="num_put__num_put"></a>  num_put::num_put  
 The constructor for objects of type `num_put`.  
  
```
explicit num_put(size_t _Refs = 0);
```  
  
### Parameters  
 `_Refs`  
 Integer value used to specify the type of memory management for the object.  
  
### Remarks  
 The possible values for the `_Refs` parameter and their significance are:  
  
-   0: The lifetime of the object is managed by the locales that contain it.  
  
-   1: The lifetime of the object must be manually managed.  
  
-   \> 0: These values are not defined.  
  
 No direct examples are possible, because the destructor is protected.  
  
 The constructor initializes its base object with **locale::**[facet](../stdcpplib/locale-class.md#facet_class)(_ *Refs*).  
  
##  <a name="num_put__put"></a>  num_put::put  
 Converts a number into a sequence of **CharType**s that represents the number formatted for a given locale.  
  
```
iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type _Dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```  
  
### Parameters  
 `_Dest`  
 An iterator addressing the first element of the inserted string.  
  
 `_Iosbase`  
 Specified the stream that contains locale with the numpunct facet used to punctuate the output and flags for formatting the output.  
  
 `_Fill`  
 A character that is used for spacing.  
  
 `val`  
 The number or Boolean type that is to be output.  
  
### Return Value  
 An output iterator the addresses the position one beyond the last element produced.  
  
### Remarks  
 All member functions return [do_put](#num_put__do_put)( `next`, `_Iosbase`, `_Fill`, `val`).  
  
### Example  
  
```  
// num_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
   basic_stringstream<char> psz2;  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << "The thousands separator is: "   
        << use_facet < numpunct <char> >(loc).thousands_sep( )   
        << endl;  
  
   psz2.imbue( loc );  
   use_facet < num_put < char > >  
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),  
                    psz2, ' ', fVal=1000.67);  
  
   if ( st & ios_base::failbit )  
      cout << "num_put( ) FAILED" << endl;  
   else  
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;  
}  
```  
  
 **The thousands separator is: .**  
**num_put( ) = 1.000,67**    
## See Also  
 [\<locale>](../stdcpplib/-locale-.md)   
 [facet Class](../stdcpplib/locale-class.md#facet_class)   
 [Thread Safety in the C++ Standard Library](../stdcpplib/thread-safety-in-the-c---standard-library.md)
