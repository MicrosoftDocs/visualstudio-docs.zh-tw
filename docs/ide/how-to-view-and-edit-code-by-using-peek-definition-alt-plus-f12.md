---
title: 使用查看定義
description: 瞭解如何使用 [查看定義] 命令來查看和編輯您的程式碼，而不需要從您目前撰寫的程式碼切換內容。
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c296aca79e6f334c93d8a9974d4a718ccd39d97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915005"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>如何：使用查看定義 (Alt+F12) 來檢視及編輯程式碼

您可以使用 [查看定義] 命令來檢視和編輯程式碼，而不需要離開撰寫中的程式碼。 [查看定義] 和 [移至定義] 會顯示相同資訊，但是 [查看定義] 是在快顯視窗中顯示，而 [移至定義] 則在個別程式碼視窗中顯示程式碼。 [移至定義] 會讓內容 (也就是作用中的程式碼視窗、目前行和游標位置) 轉換成定義程式碼視窗。 使用 [查看定義] 可以檢視和編輯該定義並在定義檔中移動，同時保留您在原始程式碼檔案中的位置。

您可以搭配使用 C#、Visual Basic 和 C++ 程式碼與 [查看定義]。 在 Visual Basic 中，[查看定義] 會針對沒有定義中繼資料的符號 (例如內建的 .NET 型別) 顯示 [物件瀏覽器] 的連結。

## <a name="use-peek-definition"></a>使用查看定義

### <a name="open-a-peek-definition-window"></a>開啟 [查看定義] 視窗

1. 您可以從想要探索的型別或成員的右鍵功能表，選擇 [查看定義] 以查看定義。 如果已啟用選項，您也可以按 **Ctrl** 鍵 (或其他輔助按鍵)，然後按一下成員名稱，以使用滑鼠查看定義。 或者，從鍵盤按下 **Alt** + **F12**。

     下圖顯示名為 `Print()` 之方法的 [查看定義] 視窗：

     ![[查看] 視窗](../ide/media/peekwindow.png)

     定義視窗會出現在原始檔案的 `printer.Print("Hello World!")` 這一行下方。 視窗不會隱藏原始檔案的任何程式碼。 `printer.Print("Hello World!")` 之後這幾行會出現在定義視窗底下。

1. 您可以將游標移至 [查看定義] 視窗中的不同位置。 您也依然可在原始程式碼視窗中四處移動。

1. 您可以從定義視窗中複製字串並貼在原始程式碼中。 您也可以從定義視窗將字串拖放至原始程式碼，而不從定義視窗刪除它。

1. 您可以選取 **ESC** 鍵或在定義視窗索引標籤上的 [關閉] 按鈕，關閉定義視窗。

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>從 [查看定義] 視窗內部開啟 [查看定義] 視窗

如果您已開啟 [查看定義] 視窗，就可以在該視窗中的程式碼上再次呼叫 [查看定義]。 另一個定義視窗隨即開啟。 一組出現在定義視窗索引標籤旁邊的階層連結點，您可以用來在定義視窗之間巡覽。 每個點的工具提示顯示點表示的定義檔檔案名稱和路徑。

   ![[查看] 視窗內的 [查看] 視窗](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>具有多個結果的查看定義

如果您在擁有多個定義的程式碼上使用 [查看定義] \(例如，部分類別\)，則結果清單會出現在程式碼定義檢視的右邊。 您可以選取清單中的所有結果，顯示它的定義。

   ![來自多個結果的 [查看] 視窗](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>在查看定義視窗中編輯

當您在 [查看定義] 視窗內開始編輯時，您所更改的檔案將以分開的索引標籤呈現在程式碼編輯器上，並且能夠反映您所做過的更改內容。 您可以在 [查看定義] 視窗中繼續進行編譯、取消和儲存變更，並且此索引標籤將繼續反映這些變更。 即使您沒有儲存變更卻關閉了 [查看定義] 視窗，您仍可以在索引標籤進行編譯、取消，並儲存變更，正確地整理您在 [查看定義] 視窗中的停止的地方。

   ![在 [查看] 視窗內編輯](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>變更查看定義的選項

1. 移至 [**工具**  >  **選項**  >  **文字編輯器**  >  **一般**]。

1. 選取 [在預覽檢視中開啟定義] 選項。

1. 按一下 **[確定]** 關閉 **[選項]** 對話方塊。

   ![設定滑鼠點按查看定義選項](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>查看定義的鍵盤快速鍵

您可以在 [查看定義] 視窗中使用這些鍵盤快速鍵：

|功能|鍵盤快速鍵|
|-------------------|:-----------------------:|
|開啟定義視窗。|**Alt** +**F12**|
|關閉定義視窗|**Esc**|
|將定義視窗升級到一般文件索引標籤|**Ctrl** +**Alt** +**首頁**|
|在定義視窗之間巡覽|**Ctrl** + + Alt **-** 和 **Ctrl** + **Alt**+**=**|
|在多個結果之間巡覽|**F8** 和 **Shift**+**F8**|
|在程式碼編輯器視窗和定義視窗之間切換|**Shift** +**Esc**|

> [!NOTE]
> 您也可以使用相同的鍵盤快速鍵，在 [查看定義] 視窗中編輯程式碼，就如同在 Visual Studio 中的其他位置使用。

## <a name="see-also"></a>另請參閱

- [巡覽程式碼](../ide/navigating-code.md)
- [移至定義和查看定義](../ide/go-to-and-peek-definition.md)
- [Visual Studio 中的生產力功能](../ide/productivity-features.md)
