---
title: 應為布林值 |Microsoft Docs
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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862653"
---
# <a name="boolean-expected"></a>必須是布林
您嘗試在 **的型別的** 物件上叫用 **valueOf** 方法，而不是 `Boolean` 。 這種調用類型的物件必須是型別 `Boolean` 。 例如：

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>更正這個錯誤

- 只在**布林值**類型的物件上叫用**valueOf** **方法。**

## <a name="see-also"></a>請參閱

- [Boolean 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Data types (資料類型)](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [控制程式流程](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [複製、傳遞和比較資料](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)