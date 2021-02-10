---
title: 靜態區域函式重構選項
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表，將區域函式設為靜態，並將函式之外定義的變數傳遞至函式的宣告與呼叫。
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 050ce5e90d9141892ff65602ca560d0add83da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967185"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>靜態區域函數重構和快速動作

本文概述與靜態區域函數相關的兩個生產力功能。 其中一個是將區域函式設為靜態的重構，另一個則是快速動作，它會產生程式碼以將變數傳遞至靜態區域函式。

## <a name="make-local-function-static"></a>將區域函式設為靜態

此重構適用於：

- C#

事項 **：** 將區域函式設為靜態，並將函數外定義的變數傳遞至函式的宣告和呼叫。

時機 **：** 您希望區域函式是靜態的，而且會在函式的範圍中定義所有變數。

**原因：** 靜態區域函式可提高可讀性：知道特定程式碼是隔離的，可讓您更容易瞭解、重新讀取和重複使用。 靜態區域函式也提供範圍，以防止使用只在單一方法中呼叫的靜態函式來污染類別。

### <a name="how-to"></a>使用方法

1. 將插入號放在區域函式名稱上。

2. 按下 **Ctrl** + **。** ) 觸發 [ **快速動作與重構** ] 功能表的 (期間。

   ![將區域函式設為靜態](media/make-local-function-static.png)

3. 選取 [ **建立區域函數 ' static ']。**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>在靜態區域函式中明確傳遞變數

此快速動作適用于：

- C#

事項 **：** 將變數明確傳遞至本機靜態函數。

時機 **：** 您希望區域函式是靜態的，但仍使用在其外部初始化的變數。

**原因：** 使用靜態區域函式可提供對讀者的澄清，因為它們知道它只能在程式的特定內容中宣告和呼叫。 它可讓您彈性地定義此內容外部的變數，但仍可將其作為靜態區域函式的引數傳遞。

### <a name="how-to"></a>使用方法

1. 將插入號放在用於靜態區域函式的變數上。

2. 按下 **Ctrl** + **。** ) 觸發 [ **快速動作與重構** ] 功能表的 (期間。

   ![在靜態區域函數中明確傳遞變數](media/pass-variable-explicitly-static-local-function.png)

3. 選取 [在本機靜態函式中明確傳遞變數]。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)