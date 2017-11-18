---
title: "prototype 屬性 （錯誤） |Microsoft 文件"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-error"></a>prototype 屬性 (錯誤)
傳回錯誤的原型參考。  
  
## <a name="syntax"></a>語法  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>備註  
 `error`引數是錯誤的名稱。  
  
 使用`prototype`屬性提供一組基本功能的錯誤。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入可傳回陣列中最大項目值的 `Error` 物件，請宣告函式，並將它加入 `Error.prototype`，然後使用它。  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件具有`prototype`是唯讀的屬性。 屬性和方法可能會加入原型，但該物件可能未獲指派不同的原型。 不過，使用者定義的物件可能會指派新的原型。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]