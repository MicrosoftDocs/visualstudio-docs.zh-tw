---
title: 產生欄位、屬性、區域變數
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d3b22f32669023666451f1981cf9c6fdf6f251e6
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483597"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>在 Visual Studio 中產生欄位、屬性或區域變數

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您針對先前未宣告的欄位、屬性或區域變數立即產生程式碼。

**時機：** 您在鍵入時引進新的欄位、屬性或區域變數，並想要自動正確地宣告這些項目。

**原因：** 您可以在使用欄位、屬性或區域變數之前先宣告這些項目；不過，此功能將自動產生宣告和類型。

## <a name="how-to"></a>操作說明

1. 將游標放在有紅色曲線的行上。 紅色波浪線表示欄位、本機或尚不存在的屬性。

   - C#: 

       ![醒目提示的程式碼 C#](media/field-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/field-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![錯誤燈泡](media/error-bulb.png) 圖示。
      - 按一下 ![錯誤燈泡](media/error-bulb.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

      ![「產生欄位/屬性/區域變數」預覽](media/field-preview-cs.png)

3. 從下拉式功能表中選取其中一個產生選項。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

   欄位、屬性或區域隨即建立，而類型會從使用方式推斷。

   - C#: 

       ![產生方法結果 C#](media/field-result-cs.png)

   - Visual Basic：

       ![產生方法結果 VB](media/field-result-vb.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)