---
title: 產生建構函式的快速動作
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a8f72638db2403b67a52ed5bc4ff005189526d7e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938350"
---
# <a name="generate-a-constructor-in-visual-studio"></a>在 Visual Studio 中產生建構函式

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您立即針對類別產生新建構函式的程式碼。

**時機：** 您引進新的建構函式並想要自動正確地宣告它，或是您修改現有的建構函式。

**原因：** 您可以在使用建構函式之前先宣告它；不過，此功能將可自動搭配正確的參數來產生建構函式。 此外，修改現有的建構函式將需要更新所有 callsite，除非您使用此功能來自動更新它們。

**做法：** 有數種產生建構函式的方式：

   - [產生建構函式並選取成員](#pick)
   - [從選取的欄位產生建構函式](#selection)
   - [從新的使用方式產生建構函式](#usage)
   - [將參數新增至現有的建構函式](#addparameter)
   - [從建構函式參數建立欄位/屬性並加以初始化](#create)

## <a id = "pick"></a> 產生建構函式並選取成員 (僅限 C#)

1. 將游標放在類別中任何空白的一行：

   ![游標在空白行中](media/constructor1-highlight-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在類別中的空白行上，此圖示就會出現在左邊界上。

   ![「產生建構函式」預覽](media/constructor1-preview-cs.png)

1. 從下拉功能表選取 [產生建構函式]。

   [選取成員] 對話方塊隨即開啟。

1. 選取您想要納入為建構函式參數的成員。 您可以使用向上鍵和向下鍵加以排序。 選擇 [確定] 。

   ![[選取成員] 對話方塊](media/constructor1-dialog-cs.png)

   > [!TIP]
   > 您可以選取 [新增 null 檢查] 核取方塊，來自動為建構函式參數產生 null 檢查。

   系統會使用指定的參數來建立建構函式。

   ![「產生建構函式」結果](media/constructor1-result-cs.png)

## <a id="selection"></a> 從選取的欄位產生建構函式 (僅限 C#)

1. 醒目提示您想要包含在所產生建構函式中的成員：

   ![醒目提示成員](media/constructor2-highlight-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在具有選取項目的行上，此圖示就會出現在左邊界上。

      ![「產生建構函式」預覽](media/constructor2-preview-cs.png)

1. 從下拉式功能表選取 [產生建構函式 'TypeName(...)']。

   系統會使用選取的參數來建立建構函式。

   ![產生建構函式結果](media/constructor2-result-cs.png)

## <a id="usage"></a> 從新的使用方式產生建構函式 (C# 和 Visual Basic)

1. 將游標放在有紅色曲線的行上。 紅色波浪線表示尚不存在的建構函式呼叫。

   - C#: 

       ![醒目提示的程式碼 C#](media/constructor-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 VB](media/constructor-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

      ![「產生建構函式」預覽](media/constructor-preview-cs.png)

3. 從下拉式功能表選取 [在 '*TypeName*' 中產生建構函式 ]。

   > [!TIP]
   > 請使用位於預覽視窗底部的 [預覽變更] 連結，以在進行選取之前先[查看將進行的所有變更](../../ide/preview-changes.md)。

   建構函式隨即建立，而任何參數會從使用方式推斷。

   - C#: 

       ![產生方法結果 C#](media/constructor-result-cs.png)

   - Visual Basic：

       ![產生方法結果 VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> 將參數新增至現有的建構函式 (僅限 C#)

1. 將參數新增至現有的建構函式呼叫。

2. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的建構函式。

    ![「產生建構函式」醒目標示](media/constructor4-highlight-cs.png)

3. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

      ![「產生建構函式」預覽](media/constructor4-preview-cs.png)

4. 從下拉式功能表選取 [將參數新增至 'TypeName(...)']。

   參數會新增至建構函式，而其類型會從使用方式推斷。

   ![「產生建構函式」結果](media/constructor4-result-cs.png)

您也可以將參數新增到現有的方法。 如需詳細資訊，請參閱[將參數新增至方法](add-parameter.md)。

## <a id="create"></a> 從建構函式參數建立欄位或屬性並加以初始化 (僅限 C#)

1. 尋找現有的建構函式並新增參數：

   ![「產生建構函式」醒目標示](media/constructor5-highlight-cs.png)

1. 將游標放在剛新增的參數內。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在具有所新增參數的行上，此圖示就會顯示在左邊界上。

   ![「產生建構函式」預覽](media/constructor5-preview-cs.png)

1. 從下拉式功能表選取 [建立和初始化屬性] 或 [建立和初始化欄位]。

   系統會宣告欄位或屬性，並自動命名以符合您的類型。 在建構函式主體中，還會新增一行程式碼以將欄位或屬性初始化。

   ![「產生建構函式」結果](media/constructor5-result-cs.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)