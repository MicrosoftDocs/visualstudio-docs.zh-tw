---
title: "規則運算式物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>規則運算式物件 (JavaScript)
此物件包含規則運算式模式，以及指出如何套用該模式的旗標。  
  
## <a name="syntax"></a>語法  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>語法  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>參數  
 *re*  
 必要項。 要指派以此規則運算式模式的變數名稱。  
  
 *模式*  
 必要項。 要使用的規則運算式模式。 如果您使用語法 1，請使用 "/" 字元分隔模式。 如果您使用語法 2，請使用引號括住模式。  
  
 `flags`  
 選擇項。 如果您使用語法 2，請使用引號括住旗標。 可用的旗標 (可能已合併) 如下：  
  
-   g (全域搜尋所有出現的*模式*)  
  
-   i (忽略大小寫)  
  
-   m (多行搜尋)  
  
-   u (unicode)，會啟用 EcmaScript 6 [Unicode 功能](../../javascript/advanced/special-characters-javascript.md)。 僅適用於 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]。  
  
-   y (原地搜尋)，只在規則運算式的 `lastIndex` 屬性中搜尋相符的項目 (而不繼續搜尋後續的索引)。 適用於 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)]。  
  
## <a name="remarks"></a>備註  
 **規則運算式**物件不應與全域混淆`RegExp`物件。 兩者看似相同，但卻完全不同。 內容**規則運算式**物件包含一個特定的唯一資訊**規則運算式**時的全域屬性的執行個體，`RegExp`物件包含發生時，持續地更新每個相符項目的資訊。  
  
 **規則運算式**物件會儲存在搜尋字串的字元組合時所使用的模式。 之後**規則運算式**建立物件，它會傳遞給字串方法，或字串會傳遞至其中一個規則運算式方法。 最近執行之搜尋的相關資訊會儲存在全域 `RegExp` 物件中。  
  
 如果您已經知道搜尋字串，請使用語法 1。 如果搜尋字串經常變更或不明 (例如來自使用者輸入的字串)，請使用語法 2。  
  
 *模式*引數編譯成內部格式，才能使用。 語法 1*模式*在載入指令碼會編譯。 語法 2*模式*編譯之前使用，或當**編譯**方法呼叫。  
  
## <a name="example"></a>範例  
 下列範例說明使用**規則運算式**所建立的物件 (re) 包含規則運算式模式及其相關聯的旗標的物件。 在此情況下，產生**規則運算式**物件接著會使用`match`方法：  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>範例  
 下列範例會更新規則運算式模式，以搜尋多個執行個體。  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>範例  
 使用 /y 旗標時，如果搜尋成功，將會在搜尋到最後一個相符項目之後，將 `lastindex` 更新為下一個字元的索引。 如果搜尋失敗，會將 `lastindex` 重設為 0。  
  
 下列範例會使用 /y 旗標及 `lastIndex` 屬性，在特定索引中搜尋相符項目。  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>屬性  
 [全域屬性](../../javascript/reference/global-property-regular-expression-javascript.md)&#124;[ignoreCase 屬性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)&#124;[multiline 屬性](../../javascript/reference/multiline-property-regular-expression-javascript.md)&#124;[source 屬性](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>方法  
 [compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md)&#124;[exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md)&#124;[測試方法](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u 旗標適用於 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]。  
  
 y 旗標適用於 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 物件](../../javascript/reference/string-object-javascript.md)