---
title: "無法指派給 &#39; 這 &#39; |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>無法指派給 &#39; 這 &#39;
您嘗試將值指派給**這**。 **這**是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]是指的關鍵字：  
  
-   目前正在執行的方法，該物件  
  
-   全域物件，如果沒有目前的方法 （或方法不屬於任何其他物件） 時。  
  
 方法是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]會透過物件叫用的函式。 在方法內，**這**關鍵字是透過叫用方法的物件的參考 (也就是要叫用類別建構函式所建立的物件**新**運算子)。  
  
 在方法內，您可以使用**這**來參考目前的物件，但是您無法指派新值給**這**。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請勿嘗試將指派給**這**。 若要存取的屬性或方法的具現化物件，使用點運算子 (例如 circle**。**半徑）。  
  
    > [!NOTE]
    >  您不能命名為使用者建立的變數**這**; 它是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]保留字。  
  
## <a name="see-also"></a>另請參閱  
 [這個陳述式](../../javascript/reference/this-statement-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)