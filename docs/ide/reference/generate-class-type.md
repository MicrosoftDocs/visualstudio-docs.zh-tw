---
title: 在 Visual Studio 中產生類別或類型
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f7b8733e6c2a1464b5ea9c07c9c9109064183a6c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296277"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>在 Visual Studio 中產生類別或類型

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即產生類別或類型的程式碼。

**時機：** 您引進新的類別或類型，並想要自動正確地宣告它。

**原因：** 您可以在使用類別或類型之前先宣告它，不過，此功能將可自動產生類別或類型。

## <a name="how-to"></a>操作說明

1. 將游標放在有紅色曲線的行上。 紅色波浪線表示尚不存在的類別。

   - C#: 

       ![醒目提示的程式碼 C#](media/class-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/class-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 出現的圖示。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在具有紅色曲線的行上，此圖示就會出現在左邊界上。

      ![「產生類別」預覽](media/class-preview-cs.png)

3. 從下拉式功能表中選取其中一個選項：

   - 在新檔案中產生 '*TypeName*' 類別&mdash;在名為 *TypeName*.cs/.vb 的檔案中建立名為 *TypeName* 的類別
   - 產生 '*TypeName*' 類別&mdash;在目前的檔案中建立名為 *TypeName* 的類別。
   - 產生巢狀類別 '*TypeName*'&mdash;在目前的類別內建立名為 *TypeName* 的巢狀類別。
   - 產生新類型...&mdash;使用您指定的所有屬性來建立新的類別或結構。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

4. 如果您選取 [產生新的類型] 項目，[產生類型] 對話方塊隨即開啟。 設定新類型的協助工具、種類及位置。

   ![產生類型](media/class-newtype-cs.png)

   選取 | 描述
   --- | ---
   存取 | 將類型設定為擁有 [預設]內部 或 [公用] 存取權。
   類型 | 這可以設定為 [類別] 或 [結構]。
   名稱 | 此名稱無法變更且將是您已經輸入的名稱。
   專案 | 如果您的方案中有多個專案，則您可以選擇要將類別/結構放在哪個專案中。
   檔案名稱 | 您可以建立新檔案，或是將類型新增至現有的檔案。

類別或結構隨即建立。 若為 C#，還會建立建構函式。

- C#

   ![產生類別結果 C#](media/class-result-cs.png)

- Visual Basic

   ![產生類別結果 VB](media/class-result-vb.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)