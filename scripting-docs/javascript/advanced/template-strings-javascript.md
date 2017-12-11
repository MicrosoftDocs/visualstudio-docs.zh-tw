---
title: "範本字串 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>範本字串 (JavaScript)
在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，您可以使用範本字串，來建構具有內嵌運算式的字串常值。 範本字串也提供對多行字串的內建支援。  
  
 若要建構範本字串，請使用抑音符號 (也稱為反勾號) (`) 括住字串，而不要使用單引號或雙引號。 下列程式碼範例顯示簡單的範本字串。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 範本字串可包含分行符號，而不需使用換行字元 (\n)。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 $ 字元用來指定範本字串中的預留位置。 語法是 ${*運算式*}，其中*運算式* 是任何 JavaScript 運算式 (例如變數或函式)，如下列範例所示。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 已加上標籤的樣板函式，可讓您使用函式修改範本字串的值，這個函式是以來自範本字串的引數叫用。 第一個引數是字串常值的陣列，它以所包含的範本字串運算式來分隔，而第二個引數為陣列 ([剩餘參數](../../javascript/functions-javascript.md))，其中包含範本字串運算式的值。  
  
 在下列範例中，已加上標籤的樣板函式 buildURL 是用來建構 URL。 語法是使用後面緊跟著範本字串的函式名稱。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 如果您需要存取傳入的原始字串值，第一個傳至已加上標籤之範本函式的引數支援 `raw` 屬性，這個屬性會傳回所傳入字串的未經處理字串形式。  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  您也可以使用 [String.raw](../../javascript/reference/string-raw-function-javascript.md) 函式，傳回範本字串的未經處理字串形式。  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 語言參考](../../javascript/javascript-language-reference.md)   
 [進階 JavaScript](../../javascript/advanced/advanced-javascript.md)