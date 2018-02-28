---
title: "條件式編譯 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConditionalComp_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, overview
- conditional compilation
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d6a5987b21afcab8c62a609dfba33f963d544de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-javascript"></a>條件式編譯 (JavaScript)
條件式編譯可使用新的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 語言功能，而不必犧牲與不支援新功能之舊版的相容性。  
  
> [!WARNING]
>  Internet Explorer 11 以前的所有 Internet Explorer 版本都支援條件式編譯。 從 Internet Explorer 11 標準模式開始以及在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式中，都不支援條件式編譯。  
  
## <a name="statements"></a>陳述式  
 您可以使用 `@cc_on` 陳述式或使用 `@if` 或 `@set` 陳述式來啟用條件式編譯。 條件式編譯的一些標準用法包括使用 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的新功能、將偵錯支援內嵌到指令碼中，以及追蹤程式碼執行。  
  
 一律將條件式編譯程式碼放入註解中，這樣一來，不支援條件式編譯的主應用程式 (例如 Netscape Navigator) 就會忽略它。 以下是一個範例。  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 這個範例使用特殊的註解分隔符號，只有在條件式編譯是由 `@cc_on` 陳述式啟用時才會使用這些分隔符號。 不支援條件式編譯的指令碼引擎只會看到表示不支援條件式編譯的訊息。