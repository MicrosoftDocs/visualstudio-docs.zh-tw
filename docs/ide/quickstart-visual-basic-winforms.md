---
title: "快速入門：使用 Visual Basic 在 Visual Studio 中建立 Windows Forms 應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: ecab13523c5d2ae362a58527f8c15ce1f26dd225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>快速入門：使用 Visual Basic 在 Visual Studio 中建立 Windows Forms 應用程式
在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立具有 Windows 使用者介面 (UI) 的簡單 Visual Basic 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案
首先，您將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案。  

1. 開啟 Visual Studio 2017。  

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。  

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [Windows 傳統桌面]。 在中間窗格中，選擇 [Windows Forms App (.NET Framework)]。 然後將檔案命名為 `HelloWorld`。  

     如果您看不到 **Windows Forms App (.NET Framework)** 專案範本，請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [Get Tools and Features (取得工具和功能)]。Visual Studio 安裝程式即會啟動。 選擇 [.NET 桌面開發] 工作負載，然後選擇 [修改]。  

     ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)  

## <a name="create-the-application"></a>建立應用程式
在您選取 Visual Basic 專案範本並命名檔案之後，Visual Studio 會為您開啟表單。 表單是 Windows 使用者介面。 我們將控制項新增至表單來建立 "Hello World" 應用程式，然後執行應用程式。   

### <a name="add-a-button-to-the-form"></a>將按鈕新增至表單  

1. 按一下 [工具箱] 開啟 [工具箱] 飛出視窗。

     ![按一下 [工具箱] 開啟 [工具箱] 視窗](../ide/media/vb-toolbox-toolwindow.png)  

     (如果看不到 [工具箱] 飛出視窗選項，則可以從功能表列開啟它。 若要這樣做，請按一下 [檢視] > [工具箱]。 或按 **Ctrl**+**Alt**+**X**)。

2. 按一下**固定**圖示，以固定 [工具箱] 視窗。

     ![按一下固定圖示，以將 [工具箱] 視窗固定到 IDE](../ide/media/vb-pin-the-toolbox-window.png)  
3. 按一下 [按鈕] 控制項，然後將它拖曳至表單。

     ![將按鈕新增至表單](../ide/media/vb-add-a-button-to-form1.png)

4. 在 [屬性] 視窗的 [外觀] 區段中，鍵入 "Click this"，然後按 **Enter** 鍵。

     ![新增表單上按鈕的文字](../ide/media/vb-button-control-text.png)  

     (如果看不到 [屬性] 視窗，則可以從功能表列開啟它。 若要這樣做，請按一下 [檢視] > [屬性視窗]。 或按 **F4** 鍵)。

5. 在 [屬性] 視窗的 [設計] 區段中，將名稱從 "Button1" 變更為 "btnClickThis"，然後按 **Enter** 鍵。

     ![新增表單上按鈕的函式](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>將標籤新增至表單
既然我們已新增可建立動作的按鈕控制項，讓我們新增可將文字傳送至其中的標籤控制項。

1. 從 [工具箱] 視窗中選取 [標籤] 控制項，然後將它拖放至表單的 [Click this] 按鈕下方。

2. 在 [屬性] 視窗的 [設計] 區段中，將名稱從 "Label1" 變更為 "lblHelloWorld"，然後按 **Enter** 鍵。

### <a name="add-code-to-the-form"></a>將程式碼新增至表單

1. 在 [Form1.vb &#91;設計&#93;] 視窗中，按兩下 [Click this] 按鈕開啟 [Form1.vb] 視窗 

      (或者，您可以在方案總管視窗中展開 **Form1.vb**，然後按一下 **Form1**)。

2. 在 **Form1.vb** 視窗中，於 **Private Sub** 行與 **End Sub** 行之間鍵入或貼上 `lblHelloWorld.Text = "Hello World!"`。

     ![將程式碼新增至表單](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>執行應用程式
1. 按一下 [啟動] 按鈕，以執行應用程式。

     ![按一下 [啟動] 偵錯和執行應用程式](../ide/media/vb-click-start-hello-world.png)

   會發生數種情況。 在 Visual Studio IDE 中，將會開啟 [診斷工具] 視窗，也會開啟 [輸出] 視窗。 但在 IDE 外部，會出現 [Form1] 對話方塊。 它將包含您的 [Click this] 按鈕，以及指出 "Label1" 的文字。

2. 按一下 [Form1] 對話方塊中的 [Click this] 按鈕。 請注意，"Label1" 文字會變更為 "Hello World!"。

    ![包含 Label1 文字的 Form1 對話方塊 ](../ide/media/vb-form1-dialog-hello-world.png)

恭喜您完成此快速入門！ 我們希望您更了解 Visual Basic 和 Visual Studio IDE。 如果您想要更深入地鑽研，請繼續目錄的＜教學課程＞一節中的教學課程。  

## <a name="see-also"></a>另請參閱   
* [快速入門：使用 Visual Basic 在 Visual Studio 中建立主控台應用程式](quickstart-visual-basic-console.md)
* [深入了解 Visual Basic IntelliSense](visual-basic-specific-intellisense.md)  
