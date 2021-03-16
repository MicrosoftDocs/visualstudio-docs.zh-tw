---
description: 您嘗試在不是布林值的物件上叫用 valueOf 方法的布林值。
title: 應為布林值 |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571437"
---
# <a name="boolean-expected"></a>必須是布林
您嘗試在 **的型別的** 物件上叫用 **valueOf** 方法，而不是 `Boolean` 。 這種調用類型的物件必須是型別 `Boolean` 。 例如：

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>更正這個錯誤

- 只在 **布林值** 類型的物件上叫用 **valueOf** **方法。**

## <a name="see-also"></a>另請參閱

- [Boolean 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Data types (資料類型)](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [控制程式流程](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [複製、傳遞和比較資料](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
