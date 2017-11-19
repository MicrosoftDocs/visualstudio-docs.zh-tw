---
title: "必須是 &#39; @&#39; |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939"></a>必須是 &#39; @&#39;
您嘗試建立用於條件式編譯陳述式中使用變數`@set`陳述式，但未將 @ 記號"**@**"變數名稱之前。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增符號"**@**"之前的變數名稱。 例如:   
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [@set陳述式](../../javascript/reference/at-set-statement-javascript.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)