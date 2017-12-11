---
title: "針對指令碼進行疑難排解 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-your-scripts-javascript"></a>指令碼疑難排解 (JavaScript)
任何程式設計語言都會有些地方有意外狀況。 例如，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的 `null` 值，其行為與 C 或 C++ 語言中的 `Null` 值不同。  
  
 以下是您在撰寫 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 指令碼時可能遇到的一些問題區域。  
  
## <a name="syntax-errors"></a>語法錯誤  
 請務必注意撰寫指令碼時的詳細資料。 例如，字串都必須包含在引號中。  
  
## <a name="order-of-script-interpretation"></a>指令碼解譯的順序  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 解譯是網頁瀏覽器之 HTML 剖析處理序的一部分。 如果您將指令碼放在文件的 \<HEAD> 標記內，則會在 \<BODY> 標記的任何部分之前進行解譯。 如果您的物件是在 \<BODY> 標記中建立，則它們在剖析 \<HEAD> 時不存在，因此無法透過指令碼操作。  
  
> [!NOTE]
>  這個行為是 Internet Explorer 所特有。 ASP 和 WSH 有不同的執行模型 (與其他主機一樣)。  
  
## <a name="automatic-type-coercion"></a>自動類型轉換  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 是含自動強制型轉的鬆散類型語言。 即使具有不同類型的值不相等，下列範例中的運算式還是會評估為 **true**。  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 若要檢查類型和值是否相同，請使用嚴格相等運算子 (===)。 下列兩個都評估為 false：  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>運算子優先順序  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)可決定運算式評估期間執行運算時。 在下列範例中，先執行乘法，再執行減法，即使減法先出現在運算式中也是一樣。  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>搭配使用 for...in 迴圈與物件  
 當您使用 [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 迴圈逐一查看物件的屬性時，無法預測或控制將物件的欄位指派給迴圈計數器變數的順序。 此外，不同語言實作的順序可能會不同。  
  
## <a name="with-keyword"></a>with 關鍵字  
 [with](../../javascript/reference/with-statement-javascript.md) 陳述式方便用於存取所指定物件中的現有屬性，但不能用來將屬性新增至物件。 若要在物件中建立新屬性，您必須特別參考物件。  
  
## <a name="this-keyword"></a>this 關鍵字  
 雖然您在物件定義內使用 `this` 關鍵字來參考物件本身，但目前執行中函式不是物件定義時，無法使用 `this` 或類似的關鍵字來參考該函式。 如果要將函式以方法形式指派給物件，您可以在函式內使用 `this` 關鍵字來參考物件。  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>撰寫可在 Internet Explorer 中撰寫程式碼的指令碼  
 如果解譯器遇到 \</SCRIPT> 標記，則此標記會終止目前指令碼。 若要顯示 "\</SCRIPT>" 本身，請將這個項目重新撰寫為至少兩個字串 (例如，"\</SCR" 和 "IPT>")，之後您可以在寫出它們的陳述式中將它們串連在一起。  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Internet Explorer 中的隱含視窗參考  
 因為一次可以開啟多個視窗，所以任何隱含視窗參考都會指向目前視窗。 針對其他視窗，您必須使用明確參考。