---
title: "normalize 方法 （字串） (JavaScript) |Microsoft 文件"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="normalize-method-string-javascript"></a>normalize 方法 (字串) (JavaScript)
傳回以 Unicode 正規化格式表示的指定字串。  
  
## <a name="syntax"></a>語法  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 要測試的字串物件。  
  
 `form`  
 選擇項。 Unicode 正規化格式值。  
  
## <a name="return-value"></a>傳回值  
 以 Unicode 正規化格式表示的指定字串。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `form` 不是支援的值，則會擲回 `RangeError`。  
  
## <a name="remarks"></a>備註  
 如果 `stringObj` 不是字串，則會轉換成字串，再由該方法嘗試傳回以 Unicode 正規化格式表示的字串。  
  
 `form`必須 Unicode 正規化格式值"NFC"、"NFD"、"NFKC"或"NFKD"對應至指定的值[Unicode 標準附錄 #15](http://www.unicode.org/reports/tr15/)。 `form` 的預設值為 "NFC"。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `normalize` 方法。  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]