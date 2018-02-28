---
title: "name 屬性 （錯誤） (JavaScript) |Microsoft 文件"
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
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>name 屬性 (錯誤) (JavaScript)
傳回錯誤的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>參數  
 `errorObj`  
 必要項。 執行個體`Error`物件。  
  
## <a name="remarks"></a>備註  
 **名稱**屬性會傳回錯誤的名稱或例外狀況型別。 發生執行階段錯誤時，會將 name 屬性設定為下列一種原生例外狀況類型：  
  
|例外狀況類型|意義|  
|--------------------|-------------|  
|ConversionError|嘗試將物件轉換成要它無法轉換的項目時，就會發生這個錯誤。|  
|RangeError|已超過允許的範圍中的引數提供給函式時，就會發生此錯誤。 例如，如果您嘗試將建構而發生此錯誤`Array`物件的長度不是有效的正整數。|  
|ReferenceError|已偵測到無效的參考時，就會發生此錯誤。 會發生這個錯誤，例如，如果預期的參考是`null`。|  
|RegExpError|規則運算式就會發生編譯錯誤時，就會發生此錯誤。 一旦編譯規則運算式，不過，不會發生此錯誤。 此範例中，就會發生，例如當規則運算式模式中有無效的語法，或旗標以外宣告**我**， **g**，或**m**，或如果它包含相同的旗標一次以上。|  
|SyntaxError|原始程式文字會剖析和該來源文字未遵循正確的語法時，就會發生此錯誤。 會發生這個錯誤，例如，如果`eval`不是有效的程式文字的引數呼叫函式。|  
|TypeError|只要運算元的實際型別不符合預期的類型，就會發生此錯誤。 發生這個錯誤狀況的範例是呼叫函式所做的項目不是物件或不支援該呼叫。|  
|URIError|偵測到不合法的 Uniform Resource Indicator (URI) 時，就會發生此錯誤。 比方說，這是錯誤的字串當中找到不合法的字元編碼或解碼時，就會發生。|  
  
## <a name="example"></a>範例  
 下例會 TypeError 擲回例外狀況是，並顯示錯誤和錯誤訊息的名稱。  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>範例  
 此程式碼的輸出如下所示。  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [description 屬性 （錯誤）](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 （錯誤）](../../javascript/reference/message-property-error-javascript.md)   
 [number 屬性 (Error)](../../javascript/reference/number-property-error-javascript.md)