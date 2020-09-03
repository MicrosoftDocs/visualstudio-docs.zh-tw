---
title: 應為 ' @ ' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814820"
---
# <a name="expected-"></a>應為 '\@'
您嘗試使用語句來建立要搭配條件式編譯語句使用的變數 `@set` ，但未在變數名稱之前放置 @ 符號 **@** 。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在 **@** 變數名稱前面緊接著加上 @ 符號。 例如：  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [@set 聲明](../../javascript/reference/at-set-statement-javascript.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)
