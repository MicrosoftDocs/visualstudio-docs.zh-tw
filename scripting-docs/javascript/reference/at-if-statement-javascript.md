---
title: "@if陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@if陳述式 (JavaScript)
根據運算式的值而定，有條件地執行陳述式群組。  
  
> [!WARNING]
>  Internet Explorer 11 標準模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援條件式編譯。 Internet Explorer 10 標準模式 (含) 以前的所有版本都支援條件式編譯。  
  
## <a name="syntax"></a>語法  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>參數  
 *condition1 condition2*  
 選擇項。 可強制轉型為布林運算式的運算式。  
  
 `text1`  
 選擇項。 如果無法剖析文字`condition1`是**true**。  
  
 `text2`  
 選擇項。 如果要剖析的文字`condition1`是**false**和`condition2`是**，則為 true**。  
  
 `text3`  
 選擇項。 如果兩個，無法剖析文字`condition1`和`condition2`是**false**。  
  
## <a name="remarks"></a>備註  
 當您撰寫 `@if` 陳述式時，不需要將每個子句分行放置。 您可以使用多個 **@elif** 子句。 不過，所有 **@elif** 子句必須在前面 **@else** 子句。  
  
 `@if` 陳述式通常會用來決定要使用多個選項中的哪個文字做為文字輸出。  
  
 通常不會在為 ASP 或 ASP.NET 網頁或命令列程式所撰寫的指令碼中使用條件式編譯變數。 這是因為編譯器的功能可以使用其他方法來決定。  
  
 當您為網頁撰寫指令碼時，一律遠將條件式編譯程式碼加入註解中。 如此可讓不支援條件式編譯的主應用程式將它忽略。  
  
## <a name="example"></a>範例  
 下列範例說明使用 **@if..。@elif..。@else...@end** 陳述式。  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>需求  
 所有 Internet Explorer 版本都支援，但是 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on陳述式](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)