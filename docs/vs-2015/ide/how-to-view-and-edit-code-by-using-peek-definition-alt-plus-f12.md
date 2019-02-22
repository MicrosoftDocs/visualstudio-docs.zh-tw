---
title: HOW TO：檢視和編輯程式碼使用查看定義 (alt+f12) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24db36d6bb3a431d5ee3848eb8a6a794980f919a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777299"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>如何：使用查看定義檢視和編輯程式碼 (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [查看定義] 命令來檢視和編輯程式碼，而不需要離開撰寫中的程式碼。 [查看定義] 和 [移至定義] 會顯示相同資訊，但是 [查看定義] 是在快顯視窗中顯示，而 [移至定義] 則在個別程式碼視窗中顯示程式碼。 [移至定義] 會讓內容 (也就是作用中的程式碼視窗、目前行和游標位置) 轉換成定義程式碼視窗。 使用 [查看定義] 可以檢視和編輯該定義並在定義檔中移動，同時保留您在原始程式碼檔案中的位置。  
  
 您可以搭配使用 C#、Visual Basic 和 C++ 程式碼與 [查看定義]。 在 Visual Basic 中，[預覽定義] 會針對沒有定義中繼資料的符號 (例如，內建的 .NET Framework 類型) 顯示 [物件瀏覽器] 的連結。  
  
> [!IMPORTANT]
>  您無法在 Visual Studio 2013 的任何 Express 版本中使用這個命令。  
  
## <a name="working-with-peek-definition"></a>使用查看定義  
  
#### <a name="to-open-a-peek-definition-window"></a>若要開啟查看定義視窗  
  
1.  您可以開啟您要探索之方法的捷徑功能表，找到 [查看定義]。 (鍵盤：Alt+F12)  
  
     下圖顯示名為 `Print()` 之方法的 [查看定義] 視窗：  
  
     ![[查看] 視窗](../ide/media/peekwindow.png "PeekWindow")  
  
     定義視窗會出現在原始檔案的 `printer.Print(“Hello World!”)` 這一行下方。 視窗不會隱藏原始檔案的任何程式碼。 `printer.Print(“Hello World!”)` 呼叫之後這幾行會出現在定義視窗底下。  
  
2.  您可以將游標移至程式碼定義視窗的不同位置。 您仍然可以在定義視窗下方或上方的原始程式碼視窗中移動。  
  
3.  您可以從定義視窗中複製字串並貼在原始程式碼中。 您也可以從定義視窗將字串拖放至原始程式碼，而不從定義視窗刪除它。  
  
4.  您可以選取 ESC 鍵或在定義視窗索引標籤上的 [關閉] 按鈕，關閉定義視窗。  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>若要從查看定義視窗內部開啟查看定義視窗  
  
-   如果您已開啟 [查看定義] 視窗，就可以在該視窗中的程式碼上再次呼叫 [查看定義]。 另一個定義視窗隨即開啟。 一組出現在定義視窗索引標籤旁邊的階層連結點，您可以用來在定義視窗之間巡覽。 每個點的工具提示顯示點表示的定義檔檔案名稱和路徑。  
  
     ![[查看] 視窗內的 [查看] 視窗](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>若要使用查看定義搭配多個結果  
  
-   如果您在擁有多個定義的程式碼上使用 [查看定義] (例如，部分類別)，則結果清單會出現在程式碼定義檢視的右邊。 您可以選取清單中的所有結果，顯示它的定義。  
  
     ![來自多個結果的 [查看] 視窗](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>若要在查看定義視窗中進行編輯  
  
-   當您在 [查看定義] 視窗內開始編輯時，您所更改的檔案將以分開的索引標籤呈現在程式碼編輯器上，並且能夠反映您所做過的更改內容。 您可以在 [查看定義] 視窗中繼續進行編譯、取消和儲存變更，並且此索引標籤將繼續反映這些變更。 即使您沒有儲存變更卻關閉了視窗，您仍可以在索引標籤做編譯、取消，並儲存變更，正確地整理您在視窗中的停止的地方。  
  
     ![在 [查看] 視窗內編輯](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>若要使用查看定義的鍵盤快速鍵  
  
-   您可以在 [查看定義] 視窗中使用這些鍵盤快速鍵：  
  
    |功能|鍵盤快速鍵|  
    |-------------------|-----------------------|  
    |開啟定義視窗。|Alt+F12|  
    |關閉定義視窗|Esc|  
    |將定義視窗升級到一般文件索引標籤|Shift+Alt+Home|  
    |在定義視窗之間巡覽|Ctrl+Alt+- 和 Ctrl+Alt+=|  
    |在多個結果之間巡覽|F8 和 Shift+F8|  
    |在程式碼編輯器視窗和定義視窗之間切換|Shift+Esc|  
  
    > [!NOTE]
    >  您也可以使用相同的鍵盤快速鍵，在 [查看定義] 視窗中編輯程式碼，就如同在 Visual Studio 中的其他位置使用。  
  
## <a name="see-also"></a>請參閱  
 [產能的秘訣](../ide/productivity-tips-for-visual-studio.md)
