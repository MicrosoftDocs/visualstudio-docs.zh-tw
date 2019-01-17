---
title: 預期的十六進位數字 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346042"
---
# <a name="expected-hexadecimal-digit"></a>必須是十六進位數
您建立不正確的 Unicode 逸出序列。 Unicode 逸出序列的開頭 \u，後面接著四個十六進位數字 （不多也不少）。 可以包含 Unicode 十六進位數字，只是數字 0-9、 大寫的字母 A-F 和小寫字母 a-f。 下列範例會示範正確的 Unicode 逸出序列。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定您 Unicode 的十六進位數字開頭 \u、 只包含數字 0-9、 大寫的字母 A-F、 小寫字母 a-f;和分為四個數字。  
  
    > [!NOTE]
    >  如果您想要在字串中，使用常值文字 \u，然後使用兩個反斜線 (\\\u)-一個用來逸出第一個反斜線。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../javascript/data-types-javascript.md)