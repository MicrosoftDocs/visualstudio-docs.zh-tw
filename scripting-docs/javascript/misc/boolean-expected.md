---
title: 需要布林值 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576051"
---
# <a name="boolean-expected"></a>必須是布林
您嘗試在 `Boolean` 以外的型別物件上叫用**valueOf**方法的**布林值。** 這種調用類型的物件必須是 `Boolean` 的類型。 例如:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>更正這個錯誤

- 只會在**布林值**類型的物件上叫用**valueOf** **方法。**

## <a name="see-also"></a>請參閱

- [Boolean 物件](../../javascript/reference/boolean-object-javascript.md)
- [資料類型](../../javascript/data-types-javascript.md)
- [控制程式流程](../../javascript/controlling-program-flow-javascript.md)
- [複製、傳遞和比較資料](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)