---
title: 將參數新增至方法的快速動作
description: 瞭解如何使用快速動作，根據使用方式，自動將參數新增至方法，並將其宣告。
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c2582228426afcefdb2587d646a8668f622309c6
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871297"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>使用快速動作將參數新增至方法

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 允許您依使用量而定，自動將參數新增至方法。

**時機：** 您必須將參數新增至方法，並想要自動正確地宣告它。

**原因：** 您可以在呼叫參數之前，將參數新增至方法宣告中，但是此功能會根據方法呼叫自動新增參數。

## <a name="how-to-use-it"></a>用法

1. 為方法呼叫新增額外的引數。

   紅色波浪線會出現在您呼叫它的方法名稱之下。

2. 將指標放在紅色波浪線上，直到 [快速動作] 功能表出現為止。 選取 [快速動作] 功能表上的 **向下鍵**，然後選取 [將參數新增至 [方法]]。

   ![在 Visual Studio 中將參數新增至方法快速動作](media/add-parameter-to-method.png)

   > [!TIP]
   > 您也可以將游標放在方法呼叫的行上，然後按下 **Ctrl**，以存取 [快速動作] 功能表 + **。**  (期間) 或選取檔案邊界中的燈泡圖示。

   Visual Studio 會將新參數新增至方法宣告中。

> [!NOTE]
> 如果您對該方法有其他呼叫，則在使用這個快速動作後，它們可能會產生錯誤，因為它們沒有為新增的參數指定引數。

## <a name="see-also"></a>另請參閱

- [將參數新增至建構函式](generate-constructor.md#addparameter)
