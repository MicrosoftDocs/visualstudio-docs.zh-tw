---
description: 您建立了不正確的 Unicode escape 序列。
title: 預期的十六進位數位 |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 107ce2dd4f9a65a0a04b8e2ec773367ffae4ce81
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570423"
---
# <a name="expected-hexadecimal-digit"></a>必須是十六進位數
您建立了不正確的 Unicode escape 序列。 Unicode escape 序列以 \u 開頭，後面接著四個十六進位數位 (不) 。 Unicode 十六進位數位只可包含數位0-9、大寫字母 A-f 和小寫字母 a-f。 下列範例示範正確格式的 Unicode escape 序列。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您的 Unicode 十六進位數位開頭為 \u、只包含數位0-9、大寫字母 A-F、小寫字母 a-f、和會分組為四位數。  
  
    > [!NOTE]
    > 如果您想要在字串中使用常值文字，請使用兩個反斜線 (\\ \u) -one 以將第一個反斜線 escape。  
  
## <a name="see-also"></a>另請參閱  
 [Data types (資料類型)](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
