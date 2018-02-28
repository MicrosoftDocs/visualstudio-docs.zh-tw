---
title: "Debug 物件 (JavaScript) |Microsoft 文件"
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
- debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Debug 物件 (JavaScript)
將輸出傳送給偵錯工具的內建全域物件。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>備註  
 您不必讓 Debug 物件執行個體化。 呼叫 `function`就可以存取其所有屬性和方法。  
  
 還有其他方式可以偵錯 Internet Explorer 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式中， `write` 物件的 `writeln` 和 `Debug` 函式會在執行階段於 Visual Studio 的 [輸出]  視窗中顯示字串。 如需有關偵錯[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式，請參閱[偵錯 Windows 通用應用程式在 Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md)。  
  
 若要偵錯 Internet Explorer 指令碼，您必須安裝指令碼偵錯工具，且指令碼必須在偵錯模式中執行。 Internet Explorer 8 和更新版本都附有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 偵錯工具。 如果使用舊版的 Internet Explorer，請參閱 [如何：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
 如不偵錯指令碼，函式就不會有任何作用。  
  
## <a name="example"></a>範例  
 這個範例使用 `write` 函式顯示變數的值。  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>常數  
 [偵錯常數](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>屬性  
 [Debug.debuggerEnabled 屬性](../../javascript/reference/debug-debuggerenabled-property.md)&#124;[Debug.setNonUserCodeExceptions 屬性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>函式  
 [Debug.msTraceAsyncCallbackStarting 函式](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md)&#124;[Debug.msTraceAsyncCallbackCompleted 函式](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md)&#124;[Debug.msTraceAsyncOperationCompleted 函式](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)&#124;[Debug.msTraceAsyncOperationStarting 函式](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md)&#124;[Debug.msUpdateAsyncCallbackRelation 函式](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)&#124;[Debug.write 函式](../../javascript/reference/debug-write-function-javascript.md)&#124;[Debug.writeln 函式](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [debugger 陳述式](../../javascript/reference/debugger-statement-javascript.md)