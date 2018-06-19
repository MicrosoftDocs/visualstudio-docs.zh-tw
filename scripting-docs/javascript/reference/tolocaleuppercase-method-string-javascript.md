---
title: toLocaleUpperCase 方法 （字串） (JavaScript) |Microsoft 文件
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640428"
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase 方法 (字串) (JavaScript)
傳回字串，其中所有字母字元已轉換成大寫，並且將主機環境的目前地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>備註  
 所需`stringVar`參考是`String`物件或字串常值。  
  
 `toLocaleUpperCase`方法會將轉換的字元在字串中，主機環境之目前地區設定列入考量。 在大部分情況下，結果會相同，因此`toUpperCase`方法。 結果會與不同語言的規則衝突的規則的 Unicode 大小寫的對應，則。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleLowerCase 方法 （字串）](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 (String)](../../javascript/reference/touppercase-method-string-javascript.md)