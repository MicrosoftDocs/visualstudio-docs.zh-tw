---
title: "toLocaleLowerCase 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase 方法 (字串) (JavaScript)
所有字母字元轉換成小寫，主機環境之目前地區設定列入考量。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>備註  
 所需`stringVar`參考是`String`物件或字串常值。  
  
 `toLocaleLowerCase`方法會將轉換的字元在字串中，主機環境之目前地區設定列入考量。 在大部分情況下，結果是相同的結果`toLowerCase`方法。 結果會與不同語言的規則衝突的規則的 Unicode 大小寫的對應，則。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleUpperCase 方法 （字串）](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)