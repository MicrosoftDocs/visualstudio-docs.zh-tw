---
title: 執行您的圖片檢視器應用程式，並嘗試其他功能
description: 執行您的圖片檢視器應用程式，並嘗試建立圖片檢視器教學課程中的其他功能。
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91488b72559b2e6deff23a5cae389cd9b4001443
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296504"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>步驟11：執行您的圖片檢視器應用程式並嘗試其他功能

您的圖片檢視器應用程式已完成，且已準備好執行。 您可以執行應用程式，並設定的背景色彩 <xref:System.Windows.Forms.PictureBox> 。 若要深入瞭解，請嘗試變更表單的色彩、自訂按鈕和核取方塊，以及變更表單的屬性，以改善應用程式。

## <a name="how-to-run-your-app-and-set-the-background-color"></a>如何執行您的應用程式並設定背景色彩

1. 選擇 **F5**，或在功能表列上依序選擇 [偵錯] > [開始偵錯]。

1. 在開啟圖片之前，請先選擇 [設定背景色彩] 按鈕。 [色彩] 對話方塊隨即開啟。

     ![[色彩] 對話方塊](../ide/media/express_colordialog.png)<br/>
***色彩** _ _dialog box *

1. 選擇色彩以設定 PictureBox 背景色彩。 請仔細查看 `backgroundButton_Click()` (或 `BackgroundButton_Click()`) 方法，以瞭解其運作方式。

    > [!NOTE]
    > 您可以將圖片的 URL 貼至 [開啟檔案] 對話方塊中，即可從網際網路載入圖片。 試著尋找透明背景的影像，以呈現您的背景色彩。

1. 選擇 [清除圖片] 按鈕，確定將圖片清除。 然後，選擇 [關閉] 按鈕來 **結束** 應用程式。

## <a name="try-other-features"></a>嘗試其他功能

* 使用 **BackColor** 屬性變更表單和按鈕的色彩。

* 使用 **Font** 和 **ForeColor** 屬性自訂按鈕和核取方塊。

* 變更表單的 **FormBorderStyle** 和 **ControlBox** 屬性。

* 使用表單的 **AcceptButton** 和 **CancelButton** 屬性，如此就會在使用者選擇 **Enter** 或 **Esc** 鍵時，自動選擇這些按鈕。 讓應用程式在使用者選擇 **Enter** 鍵時開啟 [**開啟** 檔案] 對話方塊，並在使用者選擇 **Esc 鍵** 時關閉方塊。

## <a name="next-steps"></a>下一步

若要深入了解，請繼續下列教學課程：

> [!div class="nextstepaction"]
> [教學課程2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)

若要回到上一個教學課程步驟，請參閱[步驟 10：撰寫其他按鈕和核取方塊的程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)。

## <a name="see-also"></a>另請參閱

* [其他 c # 教學課程](../get-started/csharp/index.yml)
* [更多 Visual Basic 教學課程](../get-started/visual-basic/index.yml)
* [C + + 教學課程](/cpp/get-started/tutorial-console-cpp)