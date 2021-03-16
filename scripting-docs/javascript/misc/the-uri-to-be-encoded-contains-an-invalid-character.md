---
description: 您嘗試將字串編碼為 URI，但它包含不正確字元。
title: 要編碼的 URI 包含不正確字元 |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73ed9a814c5d608df1a9686c2b61166d664115f7
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570657"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>要編碼的 URI 包含無效的字元
您嘗試將字串編碼為 (統一資源識別項) 的 URI，但它包含不正確字元。 雖然大部分字元在字串中都是有效的，以轉換成 Uri，但某些 Unicode 字元序列是不合法的。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 確定要編碼的字串只包含有效的 Unicode 序列。 完整的 URI 是由一系列的元件和分隔符號所組成。 角括弧中的名稱代表元件，而 "："、"/"、";" 和 "？" 是用來做為分隔符號的保留字元。 一般形式為：  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [encodeURI 函式](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent 函式](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)
