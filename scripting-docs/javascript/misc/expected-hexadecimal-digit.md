---
title: 預期的十六進位數字 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: e5cf7d77853cb200afe568656e1055459acad7d1
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842282"
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