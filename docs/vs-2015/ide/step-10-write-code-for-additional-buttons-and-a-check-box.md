---
title: 步驟 10：撰寫其他按鈕和核取方塊的程式碼 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851601"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>步驟 10：撰寫其他按鈕和核取方塊的程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

現在，您可以準備完成其他四個方法。 您可以複製及貼上此程式碼，但如果想要充分學習本教學課程，請輸入程式碼並使用 IntelliSense。

 這個程式碼會在您之前加入的按鈕上加入功能。 若沒有這個程式碼，按鈕就不會有任何作用。 按鈕會在其 `Click` 事件中使用程式碼 (而核取方塊會使用 `CheckChanged` 事件)，在您啟動控制項時執行不同的動作。 例如，`clearButton_Click` 事件會在您選擇 [清除圖片] 按鈕時啟動，藉由將目前影像的 `Image` 屬性設為 `null` (或 `nothing`) 清除該影像。 程式碼中的每個事件都包括註解，用於說明程式碼的功能。

 ![影片連結](../data-tools/media/playvideo.gif "PlayVideo")如需本主題的影片版本，請參閱[教學課程1：在 Visual Basic 中建立圖片檢視器-影片 5](https://msdn.microsoft.com/vbasic/gg315356.aspx)或[教學課程1：建立C#圖片檢視器-影片 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

> [!NOTE]
> 最好的做法是永遠為程式碼加上註解。 註解是供使用者閱讀的資訊，值得花時間讓您的程式碼變得更易於理解。 程式會忽略註解行上的任何文字。 在 Visual C# 中，在一行的開頭輸入兩個斜線 (//)，即可將此行變成註解，在 Visual Basic 中，在一行的開頭加上單引號 (') 可將一行變成註解。

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>若要為其他按鈕和核取方塊撰寫程式碼

- 將下列程式碼加入至 Form1 程式碼檔 (Form1.cs 或 Form1.vb)。 選擇 [VB] 索引標籤檢視 Visual Basic 程式碼。

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移到下一個教學課程步驟，請參閱[步驟 11：執行您的程式並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)。

- 若要回到上一個教學課程步驟，請參閱[步驟 9：檢閱、註解和測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)。
