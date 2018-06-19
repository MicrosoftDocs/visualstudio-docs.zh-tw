---
title: length 屬性 （字串） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638168"
---
# <a name="length-property-string-javascript"></a>length 屬性 (字串) (JavaScript)
傳回 `String` 物件的長度。  
  
> [!WARNING]
>  JavaScript 字串是不可變的因此無法修改字串的長度。  
  
## <a name="syntax"></a>語法  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>備註  
 `length`屬性包含一個整數，表示中的字元數`String`物件。 中的最後一個字元`String`物件具有索引為我`length`-1。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`length`。 JavaScript 字串是不可變的而且無法就地修改。 不過，您可以在其中寫入反轉的字串陣列，然後呼叫`join`空白的字元，這會產生任何分隔字元的字串。  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]