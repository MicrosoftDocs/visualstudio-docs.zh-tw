---
title: 必須是布林 |Microsoft Docs
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
ms.openlocfilehash: 261cf0ad93208c0eac09e42dcd68853352318e88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817896"
---
# <a name="boolean-expected"></a>必須是布林
您嘗試叫用**Boolean.prototype.toString**或是**Boolean.prototype.valueOf**以外的類型的物件上的方法`Boolean`。 這種類型的引動過程的物件必須是型別`Boolean`。 例如：

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>更正這個錯誤

- 只能叫用**Boolean.prototype.toString**或是**Boolean.prototype.valueOf**類型的物件上的方法**布林值。**

## <a name="see-also"></a>另請參閱

- [Boolean 物件](../../javascript/reference/boolean-object-javascript.md)
- [資料類型](../../javascript/data-types-javascript.md)
- [控制程式流程](../../javascript/controlling-program-flow-javascript.md)
- [複製、傳遞和比較資料](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)