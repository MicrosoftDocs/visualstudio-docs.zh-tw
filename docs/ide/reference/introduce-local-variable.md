---
title: 引進區域變數
description: 產生區域變數來取代現有的運算式。 選取運算式、按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後選取 [為所有出現 'expression' 之處引進區域]。
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 35850293b1ef739506fe6848e000396f6bacf1d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852293"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>在 Visual Studio 中引進區域變數

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即產生區域變數來取代現有的運算式。

**時機：** 您有只要放在區域變數中便可在稍後輕鬆重複使用的程式碼。

**原因：** 您可以多次複製和貼上程式碼以在各種位置中使用該程式碼，不過，最好只執行該作業一次，將結果儲存在區域變數中，然後全程使用區域變數。

## <a name="how-to"></a>使用方法

1. 醒目標示您想要指派給新區域變數的運算式。

   - C#：

       ![醒目提示的程式碼 C#](media/local-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/local-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![顯示在 [快速動作] 和 [重構] 功能表左邊界中的螺絲起子圖示螢幕擷取畫面。](media/screwdriver.png) 圖示，如果文字游標已經在含有醒目提示運算式的行上，此圖示就會出現在左邊界上。

   ![「引進區域」預覽](media/local-preview-cs.png)

3. 從下拉式功能表中，選取 [ **為 (的所有出現位置]) [引進本機** ]。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

   區域變數隨即建立，而類型會從使用方式推斷。 為新區域變數提供新名稱。

   - C#：

       ![實作介面結果 C#](media/local-result-cs.png)

   - Visual Basic：

       ![實作介面結果 VB](media/local-result-vb.png)

   > [!NOTE]
   > 您可以使用 [...所有出現之處...] 功能表選項來取代每個所選運算式，而不只是您已明確醒目提示的運算式。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
