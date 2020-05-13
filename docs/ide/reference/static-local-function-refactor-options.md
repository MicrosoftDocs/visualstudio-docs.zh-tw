---
title: 靜態區域函式重構選項
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144842"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>靜態局部函數重構和快速操作

本文概述了與靜態局部函數相關的兩個生產力功能。 一個是使局部函數成為靜態的重構，另一個是快速操作，它生成代碼將變數傳遞到靜態局部函數中。

## <a name="make-local-function-static"></a>將區域函式設為靜態

此重構適用於：

- C#

**內容：** 使局部函數成為靜態函數，並將在函數外部定義的變數傳遞給函數的聲明和調用。

**何時：** 您希望本地函數是靜態的，並且希望在函數的範圍內定義所有變數。

**原因：** 靜態本地函數提高了可讀性：知道特定代碼是隔離的，可以更容易理解、重讀和重用。 靜態局部函數還提供範圍界定，以防止使用僅在單個方法中調用的靜態函數污染類。

### <a name="how-to"></a>操作方式

1. 將您的護理放在本地函數名稱上。

2. 按**Ctrl**+**。** （期間）以觸發**快速操作和重構**功能表。

   ![將區域函式設為靜態](media/make-local-function-static.png)

3. 選擇 **"使局部函數為"靜態"。**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>在靜態局部函數中顯式傳遞變數

此快速操作適用于：

- C#

**內容：** 將變數顯式傳遞到本地靜態函數中。

**何時：** 您希望本地函數是靜態的，但仍使用在它外部初始化的變數。

**原因：** 使用靜態本地函數向讀者提供說明，因為他們知道只能在程式的特定上下文中聲明和調用它。 它提供了在此上下文之外定義變數的靈活性，但仍能夠將它們作為參數傳遞給靜態局部函數。

### <a name="how-to"></a>操作方式

1. 將圖子放在靜態局部函數中使用的變數上。

2. 按**Ctrl**+**。** （期間）以觸發**快速操作和重構**功能表。

   ![在靜態局部函數中顯式傳遞變數](media/pass-variable-explicitly-static-local-function.png)

3. 選取 [在本機靜態函式中明確傳遞變數]****。

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)