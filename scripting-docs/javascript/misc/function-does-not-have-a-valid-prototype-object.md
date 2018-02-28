---
title: "函式沒有有效的原型物件 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>函式沒有有效的原型物件
您嘗試使用**instanceof**來判斷是否物件衍生自特定函式類別，但您重新定義的物件`prototype`，可能是屬性`null`，或外部物件的類型 (這兩個不是有效[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件)。 從主控件物件模型 （例如，Internet Explorer 文件或視窗物件） 的物件或外部的 COM 物件，可以是外部的物件。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確認函式的`prototype`屬性參考到有效[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件。  
  
## <a name="see-also"></a>另請參閱  
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)