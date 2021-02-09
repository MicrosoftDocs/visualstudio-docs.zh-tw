---
title: 步驟 7：將對話方塊元件新增至您的表單
description: 瞭解如何將 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊元件和 <xref:System.Windows.Forms.ColorDialog> 對話方塊元件新增至您的表單。
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a485433ef73ef853a186a5b441396f6d5a57f679
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868851"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>步驟 7：將對話方塊元件新增至您的表單

若要讓您的應用程式開啟圖片檔並選擇背景色彩，請在此步驟中，將 <xref:System.Windows.Forms.OpenFileDialog> 元件和 <xref:System.Windows.Forms.ColorDialog> 元件新增至您的表單。

元件在某些方面就像控制項一樣。 您可以使用 [工具箱] 將元件新增至表單，並使用 [屬性] 視窗設定該元件的屬性。 但與控制項不同，將元件加入至表單並不會加入可讓使用者在表單上看見的項目。 相反地，只會提供可讓您透過程式碼來觸發的某些行為。 它是一個可開啟 [開啟檔案] 對話方塊的元件。

## <a name="to-add-dialog-components-to-your-form"></a>若要將對話方塊元件加入至您的表單

1. 選擇 [ **Windows Form 設計工具** **] (Form1.cs [Design]**) ，然後開啟 [**工具箱**] 中的 [**對話方塊**] 群組。

    > [!NOTE]
    > [工具箱] 中的 [對話方塊] 群組包含可開啟許多實用對話方塊的元件，您可用來開啟和儲存檔案、瀏覽資料夾及選擇字型和色彩。 您在本專案中會使用下列兩個對話方塊元件：OpenFileDialog 和 ColorDialog。

1. 若要將名稱為 **openFileDialog1** 的元件新增至表單，請按兩下 **OpenFileDialog**。 若要將名稱為 **colorDialog1** 的元件新增至表單，請按兩下 [工具箱] 中的 **ColorDialog**。  (您在下一個教學課程步驟中使用該帳戶。 ) 您應該會在 **圖片檢視器** 表單下方看到 **Windows Form 設計工具** (底部的區域) ，其中每個您新增的兩個對話方塊元件都有一個圖示，如下圖所示。

     ![對話方塊元件](../ide/media/express_dialogsadded.png)<br>***對話方塊** _ _components *

1. 選擇 **Windows Forms 設計工具** 底部區域中的 **openFileDialog1** 圖示。 設定兩個屬性：

    - 將 [篩選條件] 屬性設定為下列值 (您可以複製並貼上)：

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - 將 [標題] 屬性設定為下列值：[選取圖片檔案]

         [篩選條件] 屬性設定會指定要在 [選取圖片檔案] 對話方塊中顯示的檔案類型。

    > [!TIP]
    > 若要查看不同應用程式中的 [開啟檔案] 對話方塊範例，請開啟記事本或小畫家，並在功能表列上依序選擇 [檔案] > [開啟舊檔]。 請注意，檔案名旁的下拉式清單可讓您選擇檔案類型。 <br/><br/>您剛剛使用 **OpenFileDialog** 元件中的 **Filter** 屬性，在您的應用程式中進行設定。 另外，請注意 [屬性] 視窗中的 [標題] 和 [篩選條件] 屬性都是粗體。 IDE 這樣做是為了讓您知道任何屬性已變更，而不再是預設值。

## <a name="next-steps"></a>下一步

* 若要移至下一個教學課程步驟，請參閱 **[步驟8：為顯示圖片按鈕事件處理常式撰寫程式碼](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**。

* 若要回到上一個教學課程步驟，請參閱[步驟 6：命名您的按鈕控制項](../ide/step-6-name-your-button-controls.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
