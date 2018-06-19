---
title: 偵錯工具陳述式 (JavaScript) |Microsoft 文件
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
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636198"
---
# <a name="debugger-statement-javascript"></a>debugger 陳述式 (JavaScript)
暫止執行。  
  
## <a name="syntax"></a>語法  
  
```  
debugger  
```  
  
## <a name="remarks"></a>備註  
 您可以在放置`debugger`陳述式暫停執行的程序中的任何位置。 使用`debugger`陳述式，類似於程式碼中設定中斷點。  
  
 `debugger`陳述式暫停執行，但不會關閉任何檔案或清除任何變數。  
  
> [!NOTE]
>  `debugger`陳述式沒有任何作用，除非指令碼進行偵錯。  
  
## <a name="example"></a>範例  
 這個範例會使用`debugger`陳述式暫停執行的每一次反覆`for`迴圈。  
  
> [!NOTE]
>  若要執行此範例中，您必須安裝指令碼偵錯工具和指令碼必須在偵錯模式中執行。  
>   
>  包含 Internet Explorer 8[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]偵錯工具。 如果使用舊版的 Internet Explorer，請參閱 [如何：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 陳述式](../../javascript/reference/javascript-statements.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)