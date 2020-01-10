---
title: 靜態區域函式重構
ms.date: 09/28/2019
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
ms.openlocfilehash: adbf84b9ae7566cd5e58a7c757ce09a37252b754
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782276"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>靜態區域函式重構和快速動作

本文概述兩個與靜態區域函式相關的生產力功能。 其中一個是讓區域函式成為靜態的重構，另一個則是快速動作，它會產生程式碼以將變數傳遞至靜態區域函式。

## <a name="make-local-function-static"></a>將區域函式設為靜態

此重構適用於：

- C#

**功能：** 讓區域函式成為靜態，並將函式外部定義的變數傳入函式的宣告，並呼叫。

時機 **：** 您希望您的區域函式是靜態的，而且所有變數都必須在函式的範圍中定義。

**原因：** 靜態區域函式可改善可讀性：瞭解特定程式碼是隔離的，讓您更容易瞭解、重新讀取和重複使用。 靜態區域函式也會提供範圍，以防止使用只在單一方法中呼叫的靜態函式來污染類別。

### <a name="how-to"></a>操作說明

1. 將您的插入號放在區域函式名稱上。

2. 在字行任何地方按 **Ctrl**+ **.** ， （期間），以觸發 [**快速動作與重構**] 功能表。

   ![將區域函式設為靜態](media/make-local-function-static.png)

3. 選取 [**設為區域函數 ' static ']。**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>在靜態區域函式中明確地傳遞變數

這個快速動作適用于：

- C#

**功能：** 將變數明確地傳遞至本機靜態函式。

時機 **：** 您希望區域函式是靜態的，但仍使用在其外部初始化的變數。

**原因：** 使用靜態區域函式可提供讀者的說明，因為它們知道只能在程式的特定內容中宣告和呼叫。 它提供在此內容之外定義變數的彈性，但仍然能夠將它們當做引數傳遞至靜態區域函式。

### <a name="how-to"></a>操作說明

1. 將插入號放在用於靜態區域函式的變數上。

2. 在字行任何地方按 **Ctrl**+ **.** ， （期間），以觸發 [**快速動作與重構**] 功能表。

   ![在靜態區域函式中明確傳遞變數](media/pass-variable-explicitly-static-local-function.png)

3. 選取 [在本機靜態函式中明確傳遞變數]。

## <a name="see-also"></a>請參閱

- [重構](../refactoring-in-visual-studio.md)