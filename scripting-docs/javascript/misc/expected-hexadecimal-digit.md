---
title: 預期的十六進位數位 |Microsoft Docs
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
ms.openlocfilehash: f6672046e0f7bf5e39c334dc0ba30f22eaff6e9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573381"
---
# <a name="expected-hexadecimal-digit"></a>必須是十六進位數
您建立了不正確的 Unicode escape 序列。 Unicode 逸出序列是以 \u 開頭，後面再加上四個十六進位數位（不超過和小於）。 Unicode 十六進位數位只能包含數位0-9、大寫字母 A-F 和小寫字母 a-f。 下列範例示範正確格式的 Unicode escape 序列。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您的 Unicode 十六進位數位是以 \u 開頭，只包含數位0-9，大寫字母 A-f，小寫字母 a-f;和會分為四位數。  
  
    > [!NOTE]
    > 如果您想要在字串中使用常值文字，請使用兩個反斜線-（\\ \u）-一個用來轉義第一個反斜線。  
  
## <a name="see-also"></a>請參閱  
 [資料類型](../../javascript/data-types-javascript.md)