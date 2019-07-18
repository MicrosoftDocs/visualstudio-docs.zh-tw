---
title: 使用 Visual Basic 建立 Windows Forms 應用程式
description: 了解如何使用 Visual Basic 在 Visual Studio 中逐步建立 Windows Forms 應用程式。
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 4619a56bfe052a1fb191af8edfd1cef8b376617b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976929"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>使用 Visual Basic 在 Visual Studio 中建立 Windows Forms 應用程式

在這個針對 Visual Studio 整合式開發環境 (IDE) 的簡短簡介中，您將建立具有 Windows 型使用者介面 (UI) 的簡單 Visual Basic 應用程式。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面免費進行安裝。

> [!NOTE]
> 本教學課程中的某些螢幕擷取畫面使用深色佈景主題。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](../ide/quickstart-personalize-the-ide.md)頁面以了解做法。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，您將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案。

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [Windows 桌面]。 在中間窗格中，選擇 [Windows Forms App (.NET Framework)]。 然後將檔案命名為 `HelloWorld`。

     如果您看不到 **Windows Forms App (.NET Framework)** 專案範本，請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [取得工具與功能]。 Visual Studio 安裝程式即會啟動。 選擇 [.NET 桌面開發] 工作負載，然後選擇 [修改]。

     ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [建立新專案]。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案] 視窗中，在搜尋方塊內輸入或鍵入 *Windows Forms*。 接下來，從語言清單中選擇 **Visual Basic**，然後從平台清單中選擇 **Windows**。 

   在您套用語言和平台的篩選條件之後，請選擇 [Windows Forms 應用程式 (.NET Framework)] 範本，然後選擇 [下一步]。

   ![選擇 Windows Forms 應用程式 (.NET Framework) 的 Visual Basic 專案範本](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > 如果您未看到 [Windows Forms 應用程式 (.NET Framework)] 範本，您可以從 [建立新專案] 視窗中安裝。 在 [找不到你要尋找的項目嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET 桌面開發**工作負載。
   > 
   > ![Visual Studio 安裝程式中的 .NET Core 工作負載](../ide/media/install-dot-net-desktop-env.png)
   >
   > 接著，選擇Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回至「[建立專案](#create-a-project)」程序中的步驟 2。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *HelloWorld*。 接著，選擇 [建立]。

   ![在 [設定您的新專案] 視窗中，以 'HelloWorld' 命名您的專案](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio 會隨即開啟您的新專案。

::: moniker-end

## <a name="create-the-application"></a>建立應用程式

在您選取 Visual Basic 專案範本並命名檔案之後，Visual Studio 會為您開啟表單。 表單是 Windows 使用者介面。 我們將控制項新增至表單來建立 "Hello World" 應用程式，然後執行應用程式。

### <a name="add-a-button-to-the-form"></a>將按鈕新增至表單

1. 按一下 [工具箱] 開啟 [工具箱] 飛出視窗。

     ![按一下 [工具箱] 開啟 [工具箱] 視窗](../ide/media/vb-toolbox-toolwindow.png)

     (如果未顯示 [工具箱] 飛出選項，您可以按 **Ctrl**+**Alt**+**X** 來開啟。)

2. 按一下**釘選**圖示，以固定 [工具箱] 視窗。

     ![按一下固定圖示，以將 [工具箱] 視窗固定到 IDE](../ide/media/vb-pin-the-toolbox-window.png)

3. 按一下 [按鈕] 控制項，然後將它拖曳至表單。

     ![將按鈕新增至表單](../ide/media/vb-add-a-button-to-form1.png)

4. 在 [屬性] 視窗的 [外觀] 區段 (或 [字型] 區段) 中，鍵入 `Click this`，然後按 **Enter** 鍵。

     ![新增表單上按鈕的文字](../ide/media/vb-button-control-text.png)

     (如果未顯示 [屬性] 視窗，您可以從功能表列開啟。 若要這樣做，請按一下 [檢視] > [屬性視窗]。 或按 **F4** 鍵)。

5. 在 [屬性] 視窗的 [設計] 區段中，將名稱從 **Button1** 變更為 `btnClickThis`，然後按 **Enter** 鍵。

     ![新增表單上按鈕的函式](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>將標籤新增至表單

既然我們已新增可建立動作的按鈕控制項，讓我們新增可將文字傳送至其中的標籤控制項。

1. 從 [工具箱] 視窗中選取 [標籤] 控制項，然後將它拖放至表單的 [按一下這裡] 按鈕下方。

2. 在 [屬性] 視窗的 [設計] 區段中，將名稱從 **Label1** 變更為 `lblHelloWorld`，然後按 **Enter** 鍵。

### <a name="add-code-to-the-form"></a>將程式碼新增至表單

1. 在 [Form1.vb &#91;設計&#93;] 視窗中，按兩下 [Click this] 按鈕開啟 [Form1.vb] 視窗 

      (或者，您可以在 [方案總管] 中展開 **Form1.vb**，然後按一下 **Form1**)。

2. 在 [Form1.vb] 視窗中，於 **Private Sub** 行與 **End Sub** 行 (或 **Public Class Form1** 行與 **End Class** 行) 之間，鍵入下列程式碼。

     ![將程式碼新增至表單](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>執行應用程式

1. 按一下 [啟動] 按鈕，以執行應用程式。

     ![按一下 [啟動] 偵錯和執行應用程式](../ide/media/vb-click-start-hello-world.png)

   會發生數種情況。 在 Visual Studio IDE 中，會開啟 [診斷工具] 視窗和 [輸出] 視窗。 但在 IDE 外部，會出現 **Form1** 對話方塊。 其中包含您的 [按一下這裡] 按鈕，以及顯示 **Label1** 的文字。

2. 按一下 [Form1] 對話方塊中的 [Click this] 按鈕。 請注意，**Label1** 文字會變更為 **Hello World!**。

    ![包含 Label1 文字的 Form1 對話方塊 ](../ide/media/vb-form1-dialog-hello-world.png)

恭喜您完成此快速入門！ 我們希望您更了解 Visual Basic 和 Visual Studio IDE。 如果您想要更深入地鑽研，請繼續目錄的＜教學課程＞一節中的教學課程。

## <a name="see-also"></a>另請參閱

* [快速入門：使用 Visual Basic 在 Visual Studio 中建立主控台應用程式](quickstart-visual-basic-console.md)
* [深入了解 Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
