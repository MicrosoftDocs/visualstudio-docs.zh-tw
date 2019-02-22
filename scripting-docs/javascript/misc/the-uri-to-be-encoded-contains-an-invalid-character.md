---
title: 要編碼的 URI 包含無效的字元 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349786"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>要編碼的 URI 包含無效的字元
您嘗試將字串編碼為 URI （統一資源識別項），但它包含無效的字元。 雖然大部分字元字串轉換成 Uri 內有效，但是某些 Unicode 字元序列是不合法的。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定要編碼的字串，包含只有有效的 Unicode 順序。 完整的 URI 被組成一連串的元件和分隔符號。 角括弧括住的名稱代表的元件，而":"，"/"，";"和"？"是用來做為分隔符號的保留的字元。 一般格式如下：  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函式](../../javascript/reference/encodeuricomponent-function-javascript.md)