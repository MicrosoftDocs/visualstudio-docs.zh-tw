---
title: 在 Visual Studio 中實作抽象類別
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4da74a60741ac33143efd7aecf0a4275185b6d3b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294692"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>在 Visual Studio 中實作抽象類別

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即產生實作抽象類別所需的程式碼。

**時機：** 您想要從抽象類別繼承。

**原因：** 您可以手動逐一實作所有抽象成員，不過，此功能將可自動產生所有方法簽章。

## <a name="how-to"></a>操作說明

1. 將游標放在有紅色曲線的行上，該曲線代表您已從抽象類別繼承，但尚未實作所有必要的成員。

   - C#: 

       ![醒目提示的程式碼 C#](media/abstract-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/abstract-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「實作類別」預覽](media/abstract-preview-cs.png)

3. 從下拉式功能表選取 [實作抽象類別]。

   > [!TIP]
   > - 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。
   > - 使用位於預覽視窗底部的 [文件]、[專案] 及 [解決方案] 連結，在從抽象類別繼承的多個類別上建立適當的方法特徵標記。

   系統會建立抽象方法特徵標記，並備妥以供實作。

   - C#: 

       ![實作類別結果 C#](media/abstract-result-cs.png)

   - Visual Basic：

       ![實作類別結果 VB](media/abstract-result-vb.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)