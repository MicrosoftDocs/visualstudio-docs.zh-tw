---
title: 必須是布林 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347927"
---
# <a name="boolean-expected"></a>必須是布林
您嘗試叫用**Boolean.prototype.toString**或是**Boolean.prototype.valueOf**以外的類型的物件上的方法`Boolean`。 這種類型的引動過程的物件必須是型別`Boolean`。 例如: 

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