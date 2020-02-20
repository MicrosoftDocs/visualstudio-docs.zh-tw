---
title: 解壓縮區域函式
description: 選取程式碼並輸入 Ctrl+R、Ctrl+M，將程式碼片段轉換成它自己的方法。
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515327"
---
# <a name="extract-local-function-refactoring"></a>解壓縮區域函數重構

此重構適用於：

- C#

**功能：** 可讓您將程式碼片段從現有的方法轉換成區域函式。

時機 **：** 在某些方法中，您有一段需要從區域函式呼叫的現有程式碼。

**原因：** 您可以複製/貼上該程式碼，但那樣會造成重複。 較好的解決方案是將該片段重構成自己的區域函式。

## <a name="how-to"></a>操作方式

1. 反白顯示要解壓縮的程式碼。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。 

3. 選取 [擷取區域函式]。

    ![解壓縮區域函式](media/extract-local-function.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
