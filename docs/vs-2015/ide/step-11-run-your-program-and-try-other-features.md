---
title: 步驟 11：執行您的程式並嘗試其他功能 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bff0467cfe9447b1cc7814d471f56ab323bb853d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851584"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>步驟 11：執行您的程式並嘗試其他功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的程式已完成，可以開始執行。 您可以執行程式並設定 PictureBox 的背景色彩。 若要進一步了解，請試著變更表單的色彩、自訂按鈕和核取方塊並變更表單的屬性，以改善程式。

 ![影片連結](../data-tools/media/playvideo.gif "PlayVideo")如需本主題的影片版本，請參閱 [教學課程1：在 Visual Basic 中建立圖片檢視器-影片 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) 或 [教學課程1：在 c # 中建立圖片檢視器-影片 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

### <a name="to-run-your-program-and-set-the-background-color"></a>若要執行程式並設定背景色彩

1. 選擇 F5，或在功能表列上依序選擇 [偵錯]**** 和 [開始偵錯]****。

2. 在開啟圖片之前，請先選擇 [設定背景色彩]**** 按鈕。 [色彩]**** 對話方塊隨即開啟。

     ![色彩對話方塊](../ide/media/express-colordialog.png "Express_ColorDialog") 色彩對話方塊

3. 選擇色彩以設定 PictureBox 背景色彩。 仔細查看 `backgroundButton_Click()` 方法以了解其運作方式。

    > [!NOTE]
    > 您可以將圖片的 URL 貼至 [開啟檔案]**** 對話方塊中，即可從網際網路載入圖片。 試著尋找透明背景的影像，以呈現您的背景色彩。

4. 選擇 [清除圖片]**** 按鈕，確定將圖片清除。 然後，選擇 [關閉]**** 按鈕結束程式。

### <a name="to-try-other-features"></a>若要嘗試其他功能

- 使用 **BackColor** 屬性變更表單和按鈕的色彩。

- 使用 **Font** 和 **ForeColor** 屬性自訂按鈕和核取方塊。

- 變更表單的 **FormBorderStyle** 和 **ControlBox** 屬性。

- 您可以使用表單的 **>acceptbutton** 和 **CancelButton** 屬性，以便在使用者選擇 ENTER 或 ESC 鍵時，自動選擇按鈕。 讓程式在使用者選擇 ENTER 鍵時開啟 [ **開啟** 檔案] 對話方塊，然後在使用者選擇 ESC 鍵時關閉對話方塊。

### <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要深入瞭解如何在 Visual Studio 中進行程式設計，請參閱程式 [設計概念](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)。

- 若要深入了解 Visual Basic，請參閱[使用 Visual Basic 開發應用程式](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f)。

- 若要深入瞭解 Visual c #，請參閱 [c # 語言簡介及 .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081)。

- 若要移至下一個教學課程，請參閱 [教學課程2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

- 若要回到上一個教學課程步驟，請參閱 [步驟10：撰寫其他按鈕和核取方塊的程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)。
