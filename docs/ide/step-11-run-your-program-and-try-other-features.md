---
title: 步驟 11：執行您的程式並嘗試其他功能
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87992bb8ab2557dbca4c8e7e3a94dd99e5de7682
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671920"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>步驟 11：執行您的程式並嘗試其他功能
您的程式已完成，可以開始執行。 您可以執行程式並設定 <xref:System.Windows.Forms.PictureBox> 的背景色彩。 若要進一步了解，請試著變更表單的色彩、自訂按鈕和核取方塊並變更表單的屬性，以改善程式。

 若要下載這個範例的完整版，請參閱[完整的圖片檢視器教學課程範例](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) \(英文\)。

 ![影片連結](../data-tools/media/playvideo.gif)如需觀看本主題的影片版本，請參閱[教學課程 1：使用 Visual Basic 建立圖片檢視器 - 影片 5](http://go.microsoft.com/fwlink/?LinkId=205216) 或[教學課程 1：使用 C# 建立圖片檢視器 - 影片 5](http://go.microsoft.com/fwlink/?LinkId=205206)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

## <a name="to-run-your-program-and-set-the-background-color"></a>若要執行程式並設定背景色彩

1.  選擇 **F5**，或在功能表列上依序選擇 [偵錯] > [開始偵錯]。

2.  在開啟圖片之前，請先選擇 [設定背景色彩] 按鈕。 [色彩] 對話方塊隨即開啟。

     ![[色彩] 對話方塊](../ide/media/express_colordialog.png)
[色彩]**** 對話方塊

3.  選擇色彩以設定 PictureBox 背景色彩。 仔細查看 `backgroundButton_Click()` 方法以了解其運作方式。

    > [!NOTE]
    >  您可以將圖片的 URL 貼至 [開啟檔案] 對話方塊中，即可從網際網路載入圖片。 試著尋找透明背景的影像，以呈現您的背景色彩。

4.  選擇 [清除圖片] 按鈕，確定將圖片清除。 然後，選擇 [關閉] 按鈕結束程式。

## <a name="to-try-other-features"></a>若要嘗試其他功能

-   使用 **BackColor** 屬性變更表單和按鈕的色彩。

-   使用 **Font** 和 **ForeColor** 屬性自訂按鈕和核取方塊。

-   變更表單的 **FormBorderStyle** 和 **ControlBox** 屬性。

-   使用表單的 **AcceptButton** 和 **CancelButton** 屬性，如此就會在使用者選擇 **Enter** 或 **Esc** 鍵時，自動選擇這些按鈕。 讓程式在使用者選擇 **Enter** 鍵時開啟 [開啟檔案] 對話方塊，以及在使用者選擇 **Esc** 鍵時關閉對話方塊。

## <a name="to-continue-or-review"></a>若要繼續或檢視

-   若要深入了解如何使用 Visual Studio 進行程式設計，請參閱[程式設計概念](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6)。

-   若要深入了解 Visual Basic，請參閱[使用 Visual Basic 開發應用程式](/dotnet/visual-basic/developing-apps/index)。

-   若要深入了解 Visual C#，請參閱 [C# 語言和 .NET Framework 簡介](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework)。

-   若要移到下一個教學課程，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

-   若要回到上一個教學課程步驟，請參閱[步驟 10：撰寫其他按鈕和核取方塊的程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)。
