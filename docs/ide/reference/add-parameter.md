---
title: 將參數新增至方法的快速動作
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: da435d5bf4e0b7239b984263838c275d3b5c9ab3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920215"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>使用快速動作將參數新增至方法

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您依使用量而定，自動將參數新增至方法。

**時機：** 您必須將參數新增至方法，並想要自動正確地宣告它。

**原因：** 您可以在呼叫參數之前，將參數新增至方法宣告，但此功能會根據方法呼叫自動新增參數。

## <a name="how-to-use-it"></a>如何使用

1. 為方法呼叫新增額外的引數。

   在您呼叫它的方法名稱下面會出現一個紅色的「曲線」。

2. 將指標置於紅色「曲線」上，直到出現 [快速動作] 功能表。 選取 [快速動作] 功能表上的**向下鍵**，然後選取 [將參數新增至 [方法]]。

   ![在 Visual Studio 中將參數新增至方法快速動作](media/add-parameter-to-method.png)

   > [!TIP]
   > 您也可以透過將游標放在方法呼叫的行上，然後按 **Ctrl**+**.** 或選取檔案邊界中的燈泡圖示，來存取 [快速動作] 功能表。

   Visual Studio 會將新參數新增至方法宣告中。

> [!NOTE]
> 如果您對該方法有其他呼叫，則在使用這個快速動作後，它們可能會產生錯誤，因為它們沒有為新增的參數指定引數。

## <a name="see-also"></a>另請參閱

- [將參數新增至建構函式](generate-constructor.md#addparameter)