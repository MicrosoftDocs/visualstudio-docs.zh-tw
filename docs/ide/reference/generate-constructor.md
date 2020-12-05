---
title: 產生建構函式的快速動作
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表，立即為類別上的新函式產生程式碼。
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 80de8b5c8b5699f4ddbf5148e16afd2da42388f2
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617548"
---
# <a name="generate-a-constructor-in-visual-studio"></a>在 Visual Studio 中產生建構函式

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即針對類別產生新建構函式的程式碼。

**時機：** 您引進新的建構函式並想要自動正確地宣告它，或是您修改現有的建構函式。

**原因：** 您可以在使用建構函式之前先宣告它，不過，此功能將可自動搭配正確的參數來產生建構函式。 此外，修改現有的建構函式將需要更新所有 callsite，除非您使用此功能來自動更新它們。

**做法：** 有數種產生建構函式的方式：

- [產生建構函式並選取成員](#pick)
- [產生具有屬性的函式](#with)
- [從選取的欄位產生函數](#selection)
- [從新的使用方式產生建構函式](#usage)
- [將參數新增至現有的建構函式](#addparameter)
- [從建構函式參數建立欄位/屬性並加以初始化](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a> 產生建構函式並選取成員 (僅限 C#)

1. 將游標放在類別中任何空白的一行：

   ![游標在空白行中](media/constructor1-highlight-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - :::image type="icon" source="media/screwdriver.png":::如果文字游標已經在類別中的空白行上，請按一下出現在左邊界中的圖示。

   ![[產生的函式] 選項的螢幕擷取畫面。](media/constructor1-preview-cs.png)

1. 從下拉功能表選取 [產生建構函式]。

   [選取成員] 對話方塊隨即開啟。

1. 選取您想要納入為建構函式參數的成員。 您可以使用向上鍵和向下鍵加以排序。 選擇 [確定]。

   ![[選取成員] 對話方塊](media/constructor1-dialog-cs.png)

   > [!TIP]
   > 您可以選取 [新增 null 檢查] 核取方塊，來自動為建構函式參數產生 null 檢查。

   系統會使用指定的參數來建立建構函式。

   ![螢幕擷取畫面，顯示已使用指定的參數建立此函式。](media/constructor1-result-cs.png)

## <a name="generate-constructor-with-properties-c-only"></a><a id = "with"></a> 只 (c # 產生具有屬性的函式) 

1. 將游標放在執行個體上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取 [ **在 (中產生 `<QualifiedName>` 具有屬性) 的** 函式。

   ![使用 properties) 選項在 Key (的 [產生函式] 的螢幕擷取畫面。](media/generate-constructor-with-properties.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a> 從選取的欄位產生建構函式 (僅限 C#)

1. 醒目提示您想要包含在所產生建構函式中的成員：

   ![醒目提示成員](media/constructor2-highlight-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - :::image type="icon" source="media/screwdriver.png":::如果文字游標已經在具有選取範圍的行上，請按一下出現在左邊界中的圖示。

      ![[產生函數人員字串字串] 選項的螢幕擷取畫面。](media/constructor2-preview-cs.png)

1. 從下拉式功能表選取 [產生建構函式 'TypeName(...)']。

   系統會使用選取的參數來建立建構函式。

   ![螢幕擷取畫面，顯示已使用選取的參數來建立此函式。](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a> 從新的使用方式產生建構函式 (C# 和 Visual Basic)

1. 將游標放在有紅色曲線的行上。 紅色波浪線表示尚不存在的建構函式呼叫。

   - C#：

       ![醒目提示的程式碼 C#](media/constructor-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/constructor-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將滑鼠停留在紅色波浪線上，然後按一下 :::image type="icon" source="media/error-bulb.png"::: 出現的圖示。
      - :::image type="icon" source="media/error-bulb.png":::如果文字游標已經在含有紅色曲線的行上，請按一下出現在左邊界中的圖示。

      ![[親自產生程式] 選項的螢幕擷取畫面。](media/constructor-preview-cs.png)

3. 從下拉式功能表選取 [在 '*TypeName*' 中產生建構函式 ]。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

   建構函式隨即建立，而任何參數會從使用方式推斷。

   - C#：

       ![產生方法結果 C#](media/constructor-result-cs.png)

   - Visual Basic：

       ![產生方法結果 VB](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a> 將參數新增至現有的建構函式 (僅限 C#)

1. 將參數新增至現有的建構函式呼叫。

2. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的建構函式。

    ![螢幕擷取畫面，顯示有紅色波浪線的行。](media/constructor4-highlight-cs.png)

3. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將滑鼠停留在紅色波浪線上，然後按一下 :::image type="icon" source="media/error-bulb.png"::: 出現的圖示。
      - :::image type="icon" source="media/error-bulb.png":::如果文字游標已經在含有紅色曲線的行上，請按一下出現在左邊界中的圖示。

      ![[將參數新增至人員字串字串] 選項的螢幕擷取畫面。](media/constructor4-preview-cs.png)

4. 從下拉式功能表選取 [將參數新增至 'TypeName(...)']。

   參數會新增至建構函式，而其類型會從使用方式推斷。

   ![螢幕擷取畫面，顯示參數已新增至函式，其型別是從其使用方式推斷而來。](media/constructor4-result-cs.png)

您也可以將參數新增到現有的方法。 如需詳細資訊，請參閱[將參數新增至方法](add-parameter.md)。

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a> 從建構函式參數建立欄位或屬性並加以初始化 (僅限 C#)

1. 尋找現有的建構函式並新增參數：

   ![顯示現有的函式的螢幕擷取畫面。](media/constructor5-highlight-cs.png)

1. 將游標放在剛新增的參數內。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - :::image type="icon" source="media/screwdriver.png":::如果文字游標已經在具有加入參數的行上，請按一下出現在左邊界中的圖示。

   ![[建立和初始化屬性存留期] 選項的螢幕擷取畫面。](media/constructor5-preview-cs.png)

1. 從下拉式功能表選取 [建立和初始化屬性] 或 [建立和初始化欄位]。

   系統會宣告欄位或屬性，並自動命名以符合您的類型。 在建構函式主體中，還會新增一行程式碼以將欄位或屬性初始化。

   ![螢幕擷取畫面，顯示欄位或屬性已宣告並自動命名以符合您的類型。](media/constructor5-result-cs.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
