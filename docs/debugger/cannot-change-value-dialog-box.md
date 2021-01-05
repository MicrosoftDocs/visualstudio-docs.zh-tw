---
title: 無法變更值對話方塊 |Microsoft Docs
description: 如果您嘗試在偵錯工具視窗或快速監看式中將變數變更為不合法的值，請檢查 [無法變更值] 對話方塊，它會出現在 Visual Studio 中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf4181d7ff56bd1a5cf3f195bcea5b02aa023629
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729050"
---
# <a name="cannot-change-value-dialog-box"></a>無法變更值對話方塊
## <a name="error"></a>錯誤
 `The value of this variable cannot be changed` &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*

 當您在偵錯工具視窗 ([自動變數]、[監看式] 或 [區域變數] 視窗) 或 [快速監看式] 對話方塊中嘗試將變數內容變更為無效值時，這個訊息方塊就會出現。 例如，如果您將整數變數的值設定成字元字串，這個訊息方塊就會出現。

## <a name="solution"></a>解決方案
 確認您輸入偵錯工具視窗或 [快速監看式] 對話方塊內的輸入內容，對於您嘗試設定的變數而言是有效的值。

## <a name="see-also"></a>請參閱

- [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)