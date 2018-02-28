---
title: "要編碼的 URI 包含無效的字元 |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>要編碼的 URI 包含無效的字元
您嘗試將字串編碼為 URI （統一資源識別項），但它包含無效的字元。 雖然大部分字元字串轉換成 Uri 內有效，但有些 Unicode 字元序列都不合法。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定要編碼的字串，包含只有有效的 Unicode 序列。 完整的 URI 是由一連串的元件和分隔符號所組成。 角括弧括住名稱代表元件，而":"，"/"，";"和"？"是做為分隔符號使用的保留的字元。 一般格式如下：  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函式](../../javascript/reference/encodeuricomponent-function-javascript.md)