---
title: 引進區域變數
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5564752fcecfe2d7a1b2d0bf7632a9cebe3d9353
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921220"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>在 Visual Studio 中引進區域變數

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即產生區域變數來取代現有的運算式。

**時機：** 您有只要放在區域變數中便可在稍後輕鬆重複使用的程式碼。

**原因：** 您可以多次複製和貼上程式碼以在各種位置中使用該程式碼；不過，最好只執行該作業一次，將結果儲存在區域變數中，然後全程使用區域變數。

## <a name="how-to"></a>操作說明

1. 醒目標示您想要指派給新區域變數的運算式。

   - C#: 

       ![醒目提示的程式碼 C#](media/local-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/local-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![出現於左邊界的螺絲起子](media/screwdriver.png) 圖示，如果文字游標已經在含有醒目提示運算式的行上，此圖示就會出現在左邊界上。

   ![「引進區域」預覽](media/local-preview-cs.png)

3. 從下拉功能表選取 [為 'expression' (的所有出現之處) 引進區域]。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

   區域變數隨即建立，而類型會從使用方式推斷。 為新區域變數提供新名稱。

   - C#: 

       ![實作介面結果 C#](media/local-result-cs.png)

   - Visual Basic：

       ![實作介面結果 VB](media/local-result-vb.png)

   > [!NOTE]
   > 您可以使用 [...所有出現之處...] 功能表選項來取代每個所選運算式，而不只是您已明確醒目提示的運算式。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)