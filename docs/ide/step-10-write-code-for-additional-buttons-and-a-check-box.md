---
title: 步驟 10：為其他按鈕及核取方塊撰寫程式碼
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53c807835af42ac09aa71eba5dac05e9606af94f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952856"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>步驟 10：為其他按鈕及核取方塊撰寫程式碼
現在，您可以準備完成其他四個方法。 您可以複製及貼上此程式碼，但如果想要充分學習本教學課程，請輸入程式碼並使用 IntelliSense。

 這個程式碼會在您之前加入的按鈕上加入功能。 若沒有這個程式碼，按鈕就不會有任何作用。 按鈕會在其 <xref:System.Windows.Forms.Control.Click> 事件中使用程式碼 (而核取方塊會使用 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件)，在您啟動控制項時執行不同的動作。 例如，當您選擇 [清除圖片] 按鈕時所啟動的 `clearButton_Click` 事件，會將目前影像的 **Image** 屬性設為 **null** (或 **nothing**)，以此來清除影像。 程式碼中的每個事件都包括註解，用於說明程式碼的功能。

 ![影片連結](../data-tools/media/playvideo.gif)如需本主題的影片版本，請參閱[教學課程 1：Create a picture viewer in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) (教學課程 1：在 Visual Basic 中建立圖片檢視器 - 影片 5) 或 [Tutorial 1:Create a picture viewer in C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206) (教學課程 1：在 C# 中建立圖片檢視器 - 影片 5)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

> [!NOTE]
>  最佳做法：一律為程式碼加上註解。 註解是供使用者閱讀的資訊，值得花時間讓您的程式碼變得更易於理解。 程式會忽略註解行上的任何文字。 在 Visual C# 中，在一行的開頭輸入兩個斜線 (//)，即可將此行變成註解，在 Visual Basic 中，在一行的開頭加上單引號 (') 可將一行變成註解。

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>若要為其他按鈕和核取方塊撰寫程式碼

-   將下列程式碼加入至 **Form1** 程式碼檔 (*Form1.cs* 或 *Form1.vb*)。 選擇 [VB] 索引標籤檢視 Visual Basic 程式碼。

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>若要繼續或檢視

-   若要前往下一個教學課程步驟，請參閱[步驟 11：執行您的程式並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)。

-   若要回到上一個教學課程步驟，請參閱[步驟 9：檢閱、註解和測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)。
