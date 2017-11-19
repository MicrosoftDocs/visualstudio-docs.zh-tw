---
title: "compare 屬性 (Intl.Collator) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>compare 屬性 (Intl.Collator)
傳回函數，比較兩個字串，使用 自動分頁器的排序次序。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>參數  
 `collatorObj`  
 必要項。 名稱`Collator`来用於比較的物件。  
  
## <a name="remarks"></a>備註  
 所傳回的函式`compare`屬性接受兩個引數，`x`和`y`，並傳回地區設定特性的比較結果`x`和`y`使用指定的選項`Collator`物件。  
  
 比較的結果會是：  
  
-   -1，否則`x`之前`y`在排序次序。  
  
-   0 （零） 如果`x`等於`y`在排序次序。  
  
-   1，否則`x`之後`y`在排序次序。  
  
## <a name="example"></a>範例  
 下列範例會建立`Collator`物件，並執行的比較。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會使用`Collator`排序陣列的物件。 此範例示範地區設定特定的差異。  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會使用`Collator`来搜尋的字串物件。  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)