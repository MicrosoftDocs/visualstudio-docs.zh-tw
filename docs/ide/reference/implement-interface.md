---
title: 實作介面
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595549"
---
# <a name="implement-an-interface-in-visual-studio"></a>在 Visual Studio 中實作介面

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即產生實作介面所需的程式碼。

**時機：** 您想要從介面繼承。

**原因：** 您可以手動逐一實作所有介面，不過，此功能將可自動產生所有方法簽章。

## <a name="how-to"></a>操作方式

1. 將游標放在有紅色曲線的行上，該曲線代表您已參考介面，但尚未實作所有必要的成員。

   - C#：

       ![醒目提示的程式碼 C#](media/interface-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/interface-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構]**** 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![錯誤燈泡](media/error-bulb.png) 圖示。
      - 按一下 ![錯誤燈泡](media/error-bulb.png) 圖示，如果文字游標已經在具有紅色曲線的行上，此圖示就會出現在左邊界上。

3. 從下拉功能表選取 [實作介面]****。

   ![實作介面預覽](media/interface-preview-cs.png)

   > [!TIP]
   > - 請使用位於預覽視窗底部的 [預覽變更]**** 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。
   > - 使用位於預覽視窗底部的 [文件]****、[專案]**** 及 [解決方案]**** 連結，在實作介面的多個類別上建立適當的方法特徵標記。

   會建立介面的方法特徵標記，並備妥以供實作。

   - C#：

       ![實作介面結果 C#](media/interface-result-cs.png)

   - Visual Basic：

       ![實作介面結果 VB](media/interface-result-vb.png)

   > [!TIP]
   > (僅限 C#) 使用 [明確實作介面]**** 選項以在每個產生的方法前面加上介面名稱，來避免名稱發生衝突。
   >
   > ![「明確實作介面」結果](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>另請參閱

- [代碼生成](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
