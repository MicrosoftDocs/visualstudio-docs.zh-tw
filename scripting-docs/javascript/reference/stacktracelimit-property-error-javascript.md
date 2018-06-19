---
title: stackTraceLimit 屬性 （錯誤） (JavaScript) |Microsoft 文件
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
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640568"
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit 屬性 (錯誤) (JavaScript)
取得或設定堆疊追蹤限制，這相當於錯誤顯示的畫面格數目。 預設限制為 10。  
  
## <a name="syntax"></a>語法  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>備註  
 您可以設定`stackTraceLimit`屬性變成任何正值介於 0 和`Infinity`。 如果`stackTraceLimit`屬性設定為 0 時，會擲回錯誤，就會顯示任何堆疊追蹤。 如果屬性設定為負數值或非數值，值會轉換為 0。 如果設為 stackTraceLimit `Infinity`，顯示整個堆疊。 否則，`ToUint32`用來將轉換的值。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定，然後取得堆疊追蹤限制。  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>需求  
 和 Internet Explorer 10 中支援[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式。  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [description 屬性 （錯誤）](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 （錯誤）](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 （錯誤）](../../javascript/reference/name-property-error-javascript.md)   
 [stack 屬性 (Error)](../../javascript/reference/stack-property-error-javascript.md)