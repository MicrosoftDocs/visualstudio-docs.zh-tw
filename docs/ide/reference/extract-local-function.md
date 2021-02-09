---
title: 擷取區域函式
description: 選取程式碼並輸入 Ctrl + R、Ctrl + M，將程式碼片段轉換成自己的函式。
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860967"
---
# <a name="extract-local-function-refactoring"></a>解壓縮區域函數重構

此重構適用於：

- C#

事項 **：** 可讓您將現有方法中的程式碼片段轉換成區域函式。

時機 **：** 在某些需要從區域函式呼叫的方法中，您有現有的程式碼片段。

**原因：** 您可以複製/貼上該程式碼，但那樣會造成重複。 更好的解決方法是將該片段重構為它自己的區域函式。

## <a name="how-to"></a>使用方法

1. 反白顯示要解壓縮的程式碼。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。 

3. 選取 [擷取區域函式]。

    ![已反白顯示行的 [Visual Studio 程式碼] 視窗的螢幕擷取畫面。 [快速動作] 和 [重構] 功能表是 [開啟]，而且已選取 [解壓縮區域函數]。](media/extract-local-function.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
