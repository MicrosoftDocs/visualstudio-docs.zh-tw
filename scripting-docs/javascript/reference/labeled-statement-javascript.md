---
title: "標記陳述式 (JavaScript) |Microsoft 文件"
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
- labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>標記陳述式 (JavaScript)
提供陳述式的識別項。  
  
## <a name="syntax"></a>語法  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>參數  
 *標籤*  
 必要項。 Labeled 陳述式時使用的唯一識別碼。  
  
 `statements`  
 選擇項。 與相關聯的一或多個陳述式*標籤*。  
  
## <a name="remarks"></a>備註  
 標籤由**中斷**和**繼續**陳述式，以指定的陳述式**中斷**和**繼續**套用。  
  
## <a name="example"></a>範例  
 下列程式碼，**繼續**陳述式是指**如**迴圈前面加上`Inner:`陳述式。 當`j`為 24，**繼續**陳述式會造成的**如**迴圈移至下一個反覆項目。 數字 21 透過 23 和 25 30 到列印在每一行。  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)