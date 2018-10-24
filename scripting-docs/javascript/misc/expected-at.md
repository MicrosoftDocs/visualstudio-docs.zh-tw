---
title: 必須是&#39;@&#39; |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856843"
---
# <a name="expected-3939"></a>必須是&#39;@&#39;
您嘗試建立一個變數來搭配使用的條件式編譯陳述式`@set`陳述式，但未將放置 at 符號 「**@**"變數的名稱前面。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增符號 」**@**"之前的變數名稱。 例如:   
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)