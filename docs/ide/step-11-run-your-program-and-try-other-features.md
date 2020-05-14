---
title: 第 11 步：運行圖片檢視器應用並嘗試其他功能
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579898"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>第 11 步：運行圖片檢視器應用並嘗試其他功能

圖片檢視器應用已完成，可以運行。 您可以運行應用並設置 的背景<xref:System.Windows.Forms.PictureBox>顏色。 要瞭解更多資訊，請嘗試通過更改表單的顏色、自訂按鈕和核取方塊以及更改表單的屬性來改進應用程式。

## <a name="how-to-run-your-app-and-set-the-background-color"></a>如何運行應用並設置背景顏色

1. 選擇 **F5**，或在功能表列上依序選擇 [偵錯]**** > [開始偵錯]****。

1. 在開啟圖片之前，請先選擇 [設定背景色彩]**** 按鈕。 [色彩]**** 對話方塊隨即開啟。

     ![[色彩] 對話方塊](../ide/media/express_colordialog.png)<br/>
***顏色****對話方塊*

1. 選擇色彩以設定 PictureBox 背景色彩。 仔細查看`backgroundButton_Click()`（或，）`BackgroundButton_Click()`方法以瞭解它的工作原理。

    > [!NOTE]
    > 您可以將圖片的 URL 貼至 [開啟檔案]**** 對話方塊中，即可從網際網路載入圖片。 試著尋找透明背景的影像，以呈現您的背景色彩。

1. 選擇 [清除圖片]**** 按鈕，確定將圖片清除。 然後，通過選擇"**關閉**"按鈕退出應用。

## <a name="try-other-features"></a>嘗試其他功能

* 使用 **BackColor** 屬性變更表單和按鈕的色彩。

* 使用 **Font** 和 **ForeColor** 屬性自訂按鈕和核取方塊。

* 變更表單的 **FormBorderStyle** 和 **ControlBox** 屬性。

* 使用表單的 **AcceptButton** 和 **CancelButton** 屬性，如此就會在使用者選擇 **Enter** 或 **Esc** 鍵時，自動選擇這些按鈕。 當使用者選擇 **"輸入"** 並關閉該框時，當使用者選擇**Esc**時，使應用打開 **"打開檔"** 對話方塊。

## <a name="next-steps"></a>後續步驟

若要深入了解，請繼續下列教學課程：

> [!div class="nextstepaction"]
> [教程 2：創建有時算數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)

若要回到上一個教學課程步驟，請參閱[步驟 10：撰寫其他按鈕和核取方塊的程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)。

## <a name="see-also"></a>另請參閱

* [更多 C# 教程](/visualstudio/get-started/csharp/)
* [更多視覺基礎教程](/visualstudio/get-started/visual-basic/)
* [C++教程](/cpp/get-started/tutorial-console-cpp)
