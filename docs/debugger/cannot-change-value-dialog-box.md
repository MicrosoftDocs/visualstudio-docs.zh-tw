---
title: 無法變更值對話方塊 |Microsoft Docs
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
ms.openlocfilehash: 97f057edefefd590c37b49d709ecf8a6e029b905
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745747"
---
# <a name="cannot-change-value-dialog-box"></a>無法變更值對話方塊
## <a name="error"></a>錯誤
 `The value of this variable cannot be changed` &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*

 當您在偵錯工具視窗 ([自動變數]、[監看式] 或 [區域變數] 視窗) 或 [快速監看式] 對話方塊中嘗試將變數內容變更為無效值時，這個訊息方塊就會出現。 例如，如果您將整數變數的值設定成字元字串，這個訊息方塊就會出現。

## <a name="solution"></a>解決方法
 確認您輸入偵錯工具視窗或 [快速監看式] 對話方塊內的輸入內容，對於您嘗試設定的變數而言是有效的值。

## <a name="see-also"></a>另請參閱

- [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)