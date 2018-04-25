---
title: 步驟 6：命名您的按鈕控制項 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d5c402439ccb30b4803a4b1863254287bc7c2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="step-6-name-your-button-controls"></a>步驟 6：命名您的按鈕控制項
表單上只有一個 PictureBox。 加入它時，IDE 會自動將它命名為 **pictureBox1**。 只有一個 CheckBox，名為 **checkBox1**。 接著，您將撰寫一些程式碼，該程式碼會參考 CheckBox 和 PictureBox。 因為這些控制項都只有一個，所以您在程式碼中看到 **pictureBox1** 或 **checkBox1** 時就知道它們代表的意義。  
  
> [!NOTE]
>  在 Visual Basic 中，任何控制項名稱的預設第一個字母都是大寫，所以是 **PictureBox1**、 **CheckBox1**，依此類推。  
  
 表單上有四個按鈕，IDE 將它們分別命名為 **button1**、 **button2**、 **button3**及 **button4**。 只從目前的名稱來看，並無法得知哪一個按鈕才是 [關閉]  按鈕，以及哪一個是 [顯示圖片]  按鈕。 這就是為按鈕控制項指定更具資訊性名稱會很有用的原因。  
  
 ![影片連結](../data-tools/media/playvideo.gif "PlayVideo")如需觀看本主題的影片版本，請參閱[教學課程 1：在 Visual Basic 中建立圖片檢視器 - 影片 3](http://go.microsoft.com/fwlink/?LinkId=205213) 或 [教學課程 1：在 C# 中建立圖片檢視器 - 影片 3](http://go.microsoft.com/fwlink/?LinkId=205202)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。  
  
### <a name="to-name-your-button-controls"></a>命名您的按鈕控制項  
  
1.  在表單上，選擇 [關閉]  按鈕。 (如果仍然已選取所有按鈕，請選擇 ESC 鍵取消選取)。在 [屬性] 視窗中捲動，直到看到 **(Name)** 屬性為止 (屬性依字母順序排列時，**(Name)** 屬性會靠近頂端)。將名稱變更為 **closeButton**，如下圖所示。  
  
     ![包含 closeButton 名稱的 [屬性] 視窗](../ide/media/express_setnameproperty.png "Express_SetNameProperty")  
包含 closeButton 名稱的 [屬性] 視窗  
  
    > [!NOTE]
    >  如果您嘗試將按鈕的名稱變更為 **closeButton**，即 close 和 Button 兩字中間加上空格，IDE 會顯示錯誤訊息：[無效的屬性值]。 控制項名稱中不允許空格 (和其他一些字元)。  
  
2.  將其他三個按鈕分別重新命名為 **backgroundButton**、 **clearButton**和 **showButton**。 您可以選擇 [屬性]  視窗中的控制項選取器下拉式清單，以驗證這些名稱。 新按鈕名稱隨即出現。  
  
3.  按兩下表單上的 [顯示圖片]  按鈕。 或者，請選擇表單上的 [顯示圖片]  按鈕，然後選擇 ENTER 鍵。 這樣做時，IDE 會在主視窗中開啟另一個名為 **Form1.cs** 的索引標籤 (如果使用 Visual Basic 則為**Form1.vb** )。 這個索引標籤會顯示表單後的程式碼檔案，如下圖所示。  
  
     ![具有 Visual C&#35; 程式碼的 Form1.cs 索引標籤](../ide/media/express_showbuttoncode.png "Express_ShowButtonCode")  
包含 Visual C# 程式碼的 [Form1.cs] 索引標籤  
  
4.  注意這部分程式碼。 (如果使用 Visual Basic，請選擇下方的 [VB]  索引標籤，以檢視 Visual Basic 版本的程式碼)。  
  
     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]  
  
     您看到稱為 `showButton_Click()`的程式碼。 當您開啟 **showButton** 按鈕的程式碼檔時，IDE 已將此加入至表單的程式碼。 在設計階段，當您開啟表單中的控制項程式碼檔案時，如果該控制項的程式碼不存在，會產生程式碼。 這個程式碼稱為 *「方法」*(method)，當您執行程式並選取控制項 (在此例中，[顯示圖片]  按鈕) 時執行它。  
  
    > [!NOTE]
    >  在本教學課程中，自動產生的 Visual Basic 程式碼已經過簡化，括弧 () 之間的任何程式碼都已移除。 在此情況下，您也可以移除相同的程式碼。 您的程式在任一情況下都可運作。 在教學課程的其餘部分，任何自動產生的程式碼也都會盡可能地簡化。  
  
5.  再次選擇 Windows 表單設計工具索引標籤 (在 Visual C# 中為**Form1.cs [設計]** ，在 Visual Basic 中為 **Form1.vb [設計]** )，然後開啟 [清除圖片]  按鈕的程式碼檔，在表單程式碼中建立它的方法。 針對其他兩個按鈕重複此步驟。 IDE 每一次都會將新的方法加入至表單的程式碼檔案。  
  
6.  若要再加入一個方法，在 [Windows Forms 設計工具] 中開啟 CheckBox 控制項的程式碼檔案，讓 IDE 加入 `checkBox1_CheckedChanged()` 方法。 每當使用者選取或清除核取方塊時就會呼叫該方法。  
  
    > [!NOTE]
    >  在設計程式時，您通常會在程式碼編輯器和 [Windows Forms 設計工具] 之間移動。 IDE 可讓您在專案中輕鬆巡覽。 使用 [方案總管]  開啟 [Windows Forms 設計工具] (在 Visual C# 中按兩下 [Form1.cs]  或在 Visual Basic 中按兩下 [Form1.vb]  )，或是在功能表列上選擇 [檢視] 、[設計工具] 。  
  
     下列顯示您在程式碼編輯器中看到的新程式碼。  
  
     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]  
  
     您加入的五個方法稱為「 *事件處理常式*」(Event Handler)，因為每當事件發生時 (例如使用者選擇按鈕或選取方塊)，程式就會呼叫這些方法。  
  
     當您在設計階段於 IDE 檢視控制項的程式碼時，Visual Studio 會加入控制項的事件處理常式方法 (如果不存在)。 例如，當您按兩下按鈕時，IDE 會為其 Click 事件加入事件處理常式 (每當使用者選擇按鈕時，就會呼叫)。 當您按兩下核取方塊時，IDE 會為其 CheckedChanged 事件加入事件處理常式 (每當使用者選取或清除方塊時，就會呼叫)。  
  
     為控制項加入事件處理常式之後，您隨時可以從 [Windows Forms 設計工具] 回到此控制項，方法是按兩下控制項，或是在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     當您建置程式時，名稱很重要，而方法 (包括事件處理常式) 則可以具有您想要的任何名稱。 當您使用 IDE 加入事件處理常式時，IDE 會根據控制項的名稱和所處理的事件來建立名稱。 例如，名稱為 **showButton** 按鈕的 Click 事件稱為 `showButton_Click()` 事件處理常式方法。 此外，方法名稱後面通常會加上左括弧和右括弧 ()，以表示目前所討論的是方法。 如果您決定要變更程式碼變數名稱，請用滑鼠右鍵按一下程式碼中的變數，然後選擇 [重構] 、[重新命名] 。 會重新命名該變數在程式碼中的所有執行個體。 請參閱[重新命名重構](../ide/reference/rename.md)以取得詳細資訊。
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
-   若要移到下一個教學課程步驟，請參閱[步驟 7：將對話方塊元件新增至您的表單](../ide/step-7-add-dialog-components-to-your-form.md)。  
  
-   若要回到上一個教學課程步驟，請參閱[步驟 5：將控制項新增至您的表單](../ide/step-5-add-controls-to-your-form.md)。