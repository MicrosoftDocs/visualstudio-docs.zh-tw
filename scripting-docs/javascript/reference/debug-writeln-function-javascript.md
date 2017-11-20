---
title: "Debug.writeln 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln 函式 (JavaScript)
將字串傳送至指令碼偵錯工具，後面接著新行字元。  
  
## <a name="syntax"></a>語法  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>參數  
 *str1，...，str2 strN*  
 選擇項。 將字串傳送至指令碼偵錯工具。  
  
## <a name="remarks"></a>備註  
 `Debug.writeln`函式會將字串，後面接著新行字元，Microsoft Script 偵錯工具在執行階段的即時運算視窗。 如果不進行偵錯指令碼，`Debug.writeln`函式沒有任何作用。  
  
 `Debug.writeln`函式是幾乎完全相同`Debug.write`函式。 唯一的差別是`Debug.write`函式不會傳送字串之後傳送新行字元。  
  
## <a name="example"></a>範例  
 這個範例會使用`Debug.writeln`函式，則 Microsoft Script Debugger 即時運算視窗中顯示變數的值。  
  
> [!NOTE]
>  若要執行此範例中，您必須安裝指令碼偵錯工具和指令碼必須在偵錯模式中執行。  
>   
>  包含 Internet Explorer 8[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]偵錯工具。 如果使用舊版的 Internet Explorer，請參閱 [如何：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**: [Debug 物件](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Debug.write 函式](../../javascript/reference/debug-write-function-javascript.md)