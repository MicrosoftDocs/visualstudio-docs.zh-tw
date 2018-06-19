---
title: toLocaleString 方法 (Object) (JavaScript) |Microsoft 文件
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
- toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640708"
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString 方法 (Object) (JavaScript)
傳回日期轉換為字串，使用目前的地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>備註  
 所需`dateObj`可以是任何`Date`物件。  
  
 `toLocaleString`方法會傳回`String`物件，其中包含寫入目前的地區設定長的預設格式的日期。  
  
-   1999 西元 1601年之間的日期，根據使用者的控制面板地區設定格式化的日期。  
  
-   超出這個範圍的預設格式的日期**toString**使用方法。  
  
 例如，在美國，`toLocaleString`傳回"01/05/96 00:00:00"為 5 年 1 月。 在歐洲，它會傳回"05/01/96 00:00:00"相同的日期、 歐洲慣例為將每月前的一天。  
  
> [!NOTE]
>  `toLocaleString`只應該用來對使用者顯示結果它應該永遠不會用於做為基礎的指令碼內的計算傳回的結果是電腦專屬。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `toLocaleString` 方法。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Array 物件](../../javascript/reference/array-object-javascript.md)&#124;[日期物件](../../javascript/reference/date-object-javascript.md)&#124;[編號物件](../../javascript/reference/number-object-javascript.md)&#124;[Object 物件](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)