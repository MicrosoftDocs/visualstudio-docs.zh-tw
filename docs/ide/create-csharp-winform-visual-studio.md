---
title: 使用 C 建立 Windows Forms 應用程式#
description: '瞭解如何在 Visual Studio 中使用 c # 逐步建立 Windows Forms 應用程式。'
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0fcc42b999039abe5d682394e378cb95f12b9283
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956928"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>使用 C 在 Visual Studio 中建立 Windows Forms 應用程式\#

在這 Visual Studio 整合式開發環境 (IDE) 的簡短簡介中，您將建立一個簡單的 c # 應用程式，其中具有以 Windows 為基礎的使用者介面 (UI) 。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

> [!NOTE]
> 本教學課程中的某些螢幕擷取畫面使用深色佈景主題。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](../ide/quickstart-personalize-the-ide.md)頁面以了解做法。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，您將建立 C# 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案。

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案]**[新增]** > **[專案]** > 。

1. 在左窗格的 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #**]，然後選擇 [ **Windows 桌面**]。 在中間窗格中，選擇 [Windows Forms App (.NET Framework)]。 然後將檔案命名為 `HelloWorld`。

     如果您看不到 **Windows Forms App (.NET Framework)** 專案範本，請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [取得工具與功能]。 Visual Studio 安裝程式即會啟動。 選擇 **.net 桌面開發** 工作負載，然後選擇 [ **修改**]。

     ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [ **建立新專案** ] 視窗中，選擇 c # 的 **Windows Forms 應用程式 ( .NET Framework)** 範本。

    (您想要的話，您可以縮小搜尋範圍，以快速取得您想要的範本。 例如，在 [搜尋] 方塊中輸入或輸入 *Windows Forms 應用程式* 。 接下來，從 [語言] 清單中選擇 [ **c #** ]，然後從 [平臺] 清單中選擇 [ **Windows** ]。 )   

   ![選擇 Windows Forms 應用程式 ( .NET Framework 的 c # 範本) ](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > 如果您未看到 [Windows Forms 應用程式 (.NET Framework)] 範本，您可以從 [建立新專案] 視窗中安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET 桌面開發** 工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)
   >
   > 接下來，選擇 Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回至「[建立專案](#create-a-project)」程序中的步驟 2。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *HelloWorld*。 然後，選擇 [ **建立**]。

   ![在 [設定您的新專案] 視窗中，以 'HelloWorld' 命名您的專案](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio 會隨即開啟您的新專案。

::: moniker-end

## <a name="create-the-application"></a>建立應用程式

選取 c # 專案範本並命名您的檔案之後，Visual Studio 會為您開啟表單。 表單是 Windows 使用者介面。 我們會將控制項新增至表單來建立 "Hello World" 應用程式，然後執行應用程式。

### <a name="add-a-button-to-the-form"></a>將按鈕新增至表單

1. 選擇 [工具箱] 以開啟 [工具箱] 飛出視窗。

     ![選擇 [工具箱] 以開啟 [工具箱] 視窗](../ide/media/csharp-toolbox-toolwindow.png)

     (如果未顯示 [工具箱] 快顯選項，您可以從功能表列開啟。 若要這樣做，請 **參閱**[  >  **工具箱**]。 或者，按下 **Ctrl** + **Alt** + **X**. ) 

1. 選擇 **釘** 選圖示以停駐 [ **工具箱** ] 視窗。

     ![選擇釘選圖示以將 [工具箱] 視窗釘選到 IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. 選擇 **按鈕** 控制項，然後將它拖曳到表單上。

     ![將按鈕新增至表單](../ide/media/csharp-add-button-form1.png)

1. 在 [ **屬性** ] 視窗中，尋找 [ **文字**]，將名稱從 **Button1** 變更為 `Click this` ，然後按 **enter**。

     ![新增表單上按鈕的文字](../ide/media/vb-button-control-text.png)

     (如果未顯示 [屬性] 視窗，您可以從功能表列開啟。 若要這樣做，請選擇 [**視圖**  >  **屬性視窗]**。 或者，按下 **F4** 鍵 ) 

1. 在 [屬性] 視窗的 [設計] 區段中，將名稱從 **Button1** 變更為 `btnClickThis`，然後按 **Enter** 鍵。

     ![新增表單上按鈕的函式](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > 如果您依字母順序排序 [ **屬性** ] 視窗中的清單，則 **Button1** 會出現在 (的 [系結 **)** ] 區段中。

### <a name="add-a-label-to-the-form"></a>將標籤新增至表單

既然我們已新增可建立動作的按鈕控制項，讓我們新增可將文字傳送至其中的標籤控制項。

1. 從 [工具箱] 視窗中選取 [標籤] 控制項，然後將它拖放至表單的 [按一下這裡] 按鈕下方。

1. 在 [**屬性**] 視窗的 [**設計**] 區段或 [ (的 [系結] **)** 區段中，將 [ **Label1** ] 的名稱變更為 `lblHelloWorld` ，然後按 **enter**。

### <a name="add-code-to-the-form"></a>將程式碼新增至表單

1. 在 [ **Form1.cs &#91;設計&#93;** ] 視窗中，按兩下 [ **按一下這個** 按鈕以開啟 [ **Form1.cs** ] 視窗。

       (另外，您也可以在 **方案總管** 中展開 [ **Form1.cs** ]，然後選擇 [ **Form1**]。 ) 

1. 在 [ **Form1.cs** ] 視窗中，于私用的 **void** 行後面輸入或輸入， `lblHelloWorld.Text = "Hello World!";` 如下列螢幕擷取畫面所示：

     ![將程式碼新增至表單](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>執行應用程式

1. 選擇 [ **開始** ] 按鈕以執行應用程式。

     ![選擇 [開始] 以偵測和執行應用程式](../ide/media/vb-click-start-hello-world.png)

   會發生數種情況。 在 Visual Studio IDE 中，會開啟 [診斷工具] 視窗和 [輸出] 視窗。 但在 IDE 外部，會出現 **Form1** 對話方塊。 其中包含您的 [按一下這裡] 按鈕，以及顯示 **Label1** 的文字。

1. 選擇 [ **Form1** ] 對話方塊中的 [**按一下這個** 按鈕]。 請注意，**Label1** 文字會變更為 **Hello World!**。

    ![包含 Label1 文字的 Form1 對話方塊 ](../ide/media/vb-form1-dialog-hello-world.png)

1. 關閉 [ **Form1** ] 對話方塊以停止執行應用程式。

## <a name="next-steps"></a>下一步

若要深入了解，請繼續下列教學課程：

> [!div class="nextstepaction"]
> [教學課程：建立圖片檢視器](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>另請參閱

* [其他 c # 教學課程](../get-started/csharp/index.yml)
* [Visual Basic 教學課程](../get-started/visual-basic/index.yml)
* [C + + 教學課程](/cpp/get-started/tutorial-console-cpp)