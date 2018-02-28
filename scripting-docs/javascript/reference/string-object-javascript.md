---
title: "字串物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>String 物件 (JavaScript)
允許處理及設定文字字串格式，以及字串內子字串的判斷和位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>參數  
 `newString`  
 必要項。 要對其指派 `String` 物件的變數名稱。  
  
 `stringLiteral`  
 選擇項。 任何 Unicode 字元群組。  
  
## <a name="remarks"></a>備註  
 您可以在字串中放入 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 提供的逸出序列 (Escape Sequence)，用來建立無法直接輸入的字元。 例如，`\t` 會指定定位字元。 如需詳細資訊，請參閱[特殊字元](../../javascript/advanced/special-characters-javascript.md)。  
  
## <a name="string-literals"></a>字串常值  
 A*字串常值*是以單引號或雙引號括住的零個或多個字元。 字串常值的主要 (基本) 資料類型為 `string`。 A*字串物件*建立使用[new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)，而且其資料類型為`Object`。  
  
 下列範例將示範字串常值的資料類型與 `String` 物件的資料類型不同。  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>字串常值的方法  
 當您在字串常值上呼叫方法時，它會暫時轉換成字串包裝函式物件。 處理字串常值的方式會像是使用 `new` 運算子建立一樣。  
  
 下列範例會將 `toUpperCase` 方法套用至字串常值。  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>存取個別字元  
 您可以將字串中的個別字元當做唯讀陣列索引屬性存取。 這個功能已在 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]中引入。 下列範例會存取個別字串字元。  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>需求  
 `String Object` 已在 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] 中引入。 下列清單中的某些成員是在後來的版本中才導入。  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>屬性  
 下表列出 `String` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[constructor 屬性](../../javascript/reference/constructor-property-string.md)|指定用來建立物件的函式。|  
|[length 屬性 (字串)](../../javascript/reference/length-property-string-javascript.md)|傳回 `String` 物件的長度。|  
|[prototype 屬性](../../javascript/reference/prototype-property-string.md)|傳回物件類別的原型參考。|  
  
## <a name="functions"></a>函式  
 下表列出 `String` 物件的函式。  
  
|函式|說明|  
|--------------|-----------------|  
|[String.fromCharCode 函式](../../javascript/reference/string-fromcharcode-function-javascript.md)|從一些 Unicode 字元值中傳回字串。|  
|[String.fromCodePoint 函式](../../javascript/reference/string-fromcodepoint-function-javascript.md)|傳回與 Unicode UTF-16 字碼指標關聯的字串。|  
|[String.raw 函式](../../javascript/reference/string-raw-function-javascript.md)|傳回原始字串形式的範本字串。|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>方法  
 下表列出 `String` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[anchor 方法](../../javascript/reference/html-tag-methods-javascript.md)|將具有 NAME 屬性的 HTML 錨點放在文字周圍。|  
|[big 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<b i g > 標籤文字周圍。|  
|[blink 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML\<閃爍 > 標籤文字周圍。|  
|[bold 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<B > 標籤文字周圍。|  
|[charAt 方法](../../javascript/reference/charat-method-string-javascript.md)|傳回指定索引中的字元。|  
|[charCodeAt 方法](../../javascript/reference/charcodeat-method-string-javascript.md)|傳回指定字元的 Unicode 編碼方式。|  
|[codePointAt 方法](../../javascript/reference/codepointat-method-string-javascript.md)|傳回 Unicode UTF-16 字元的字碼指標。|  
|[concat 方法 (字串)](../../javascript/reference/concat-method-string-javascript.md)|傳回字串，其中包含兩個所提供字串的串連。|  
|[endsWith 方法](../../javascript/reference/endswith-method-string-javascript.md)|傳回布林值，指出字串或子字串的結尾是否為傳入的字串。|  
|[includes 方法](../../javascript/reference/includes-method-string-javascript.md)|傳回布林值，指出字串物件中是否包含傳入的字串。|  
|[fixed 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<TT > 標籤文字周圍。|  
|[fontcolor 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML\<字型 > 標記具有 COLOR 屬性文字周圍。|  
|[fontsize 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML\<字型 > 標記具有 SIZE 屬性文字周圍。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[indexOf 方法 (字串)](../../javascript/reference/indexof-method-string-javascript.md)|傳回子字串第一次出現在字串中的字元位置。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型鏈結中。|  
|[italics 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML\<我 > 標籤文字周圍。|  
|[lastIndexOf 方法 (字串)](../../javascript/reference/lastindexof-method-string-javascript.md)|傳回子字串在字串中最後一個出現的位置。|  
|[link 方法](../../javascript/reference/html-tag-methods-javascript.md)|將具有 HREF 屬性的 HTML 錨點放在文字周圍。|  
|[localeCompare 方法](../../javascript/reference/localecompare-method-string-javascript.md)|傳回值，這個值指出兩個字串在目前地區設定中是否相等。|  
|[match 方法](../../javascript/reference/match-method-string-javascript.md)|使用提供的搜尋字串**規則運算式**物件，並傳回結果做為陣列。|  
|[normalize 方法](../../javascript/reference/normalize-method-string-javascript.md)|傳回以 Unicode 正規化格式表示的指定字串。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可以列舉。|  
|[repeat 方法](../../javascript/reference/repeat-method-string-javascript.md)|傳回新的字串物件，其值等於原始字串重複指定的次數。|  
|[replace 方法](../../javascript/reference/replace-method-string-javascript.md)|使用規則運算式取代字串中的文字，並傳回結果。|  
|[search 方法](../../javascript/reference/search-method-string-javascript.md)|傳回規則運算式搜尋中第一個符合子字串的位置。|  
|[slice 方法 (字串)](../../javascript/reference/slice-method-string-javascript.md)|傳回字串的一個區段。|  
|[small 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML\<小 > 標籤文字周圍。|  
|[split 方法](../../javascript/reference/split-method-string-javascript.md)|在字串分割為子字串之後，傳回所產生的字串陣列。|  
|[startsWith 方法](../../javascript/reference/startswith-method-string-javascript.md)|傳回布林值，指出字串或子字串的開頭是否為傳入的字串。|  
|[strike 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<STRIKE > 標籤文字周圍。|  
|[sub 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<SUB > 標籤文字周圍。|  
|[substr 方法](../../javascript/reference/substr-method-string-javascript.md)|傳回從指定位置起始且具有指定長度的子字串。|  
|[substring 方法](../../javascript/reference/substring-method-string-javascript.md)|傳回 `String` 物件中指定位置上的子字串。|  
|[sup 方法](../../javascript/reference/html-tag-methods-javascript.md)|將 HTML \<SUP > 標籤文字周圍。|  
|[toLocaleLowerCase 方法](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|傳回字串，其中所有字母字元都會轉換成小寫，並且將主機環境的目前地區設定列入考慮。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|傳回使用目前地區設定轉換為字串的物件。|  
|[toLocaleUpperCase 方法](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|傳回字串，其中所有字母字元都會轉換成大寫，並且將主機環境的目前地區設定列入考慮。|  
|[toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)|傳回所有字母字元都轉換成小寫的字串。|  
|[toString 方法](../../javascript/reference/tostring-method-string-1.md)|傳回字串。|  
|[toUpperCase 方法](../../javascript/reference/touppercase-method-string-javascript.md)|傳回所有字母字元都轉換成大寫的字串。|  
|[trim 方法](../../javascript/reference/trim-method-string-javascript.md)|傳回已移除前後空白字元及行結束字元的字串。|  
|[valueOf 方法](../../javascript/reference/valueof-method-string.md)|傳回字串。|  
  
## <a name="see-also"></a>另請參閱  
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [捲動、 移動和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)