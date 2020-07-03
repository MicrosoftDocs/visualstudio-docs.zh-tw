---
title: Hello World 延伸模組教學課程 |Microsoft Docs
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 796cb53ea5124662c695cce55241794802f042c0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905934"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>教學課程-建立您的第一個擴充功能： Hello World

此 Hello World 範例會逐步引導您建立 Visual Studio 的第一個延伸模組。 本教學課程說明如何將新的命令加入 Visual Studio。

在此過程中，您將瞭解如何：

* **[建立擴充性專案](#create-an-extensibility-project)**
* **[新增自訂命令](#add-a-custom-command)**
* **[修改原始程式碼](#modify-the-source-code)**
* **[加以執行](#run-it)**

在此範例中，您將使用 Visual c # 新增名為「說 Hello World！」的自訂功能表按鈕。 如下所示：

![Hello World 命令](media/hello-world-say-hello-world.png)

> [!NOTE]
> 本文適用于 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱[Visual Studio for Mac 中](/visualstudio/mac/extending-visual-studio-mac-walkthrough)的擴充性逐步解說。

## <a name="prerequisites"></a>必要條件

開始之前，請確定您已安裝**Visual Studio 延伸模組開發**工作負載，其中包含您需要的 VSIX 範本和範例程式碼。

> [!NOTE]
> 您可以使用任何版本的 Visual Studio （「社區」、「專業」或「企業」）來建立 Visual Studio 擴充性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性專案

::: moniker range="vs-2017"

步驟 1： 從 [檔案]**** 功能表選取 [新增]**** > [專案]****。

步驟 2： 在右上方的 [搜尋] 方塊中，輸入 "vsix"，然後選取 [Visual c # **vsix] 專案**。 在對話方塊底部輸入 "HelloWorld" 作為**名稱**，然後選取 **[確定]**。

![新增專案](media/hello-world-new-project.png)

您現在應該會看到 [消費者入門] 頁面和一些範例資源。

如果您需要離開本教學課程並回頭返回，您可以在 [**開始] 頁面**的 [**最近**] 區段中找到新的 HelloWorld 專案。

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 從 [檔案]**** 功能表選取 [新增]**** > [專案]****。 搜尋 "vsix" 並選取 [Visual c # **vsix] 專案**，然後選取 [**下一步]**。

步驟 2： 輸入 "HelloWorld" 作為**專案名稱**，然後選取 [**建立**]。

![新增專案](media/hello-world-new-project-2019.png)

您現在應該會在**方案總管**中看到 HelloWorld 專案。

::: moniker-end

## <a name="add-a-custom-command"></a>新增自訂命令

步驟 1： 如果您選取*extension.vsixmanifest*資訊清單檔，您可以看到哪些選項可變更，例如 [描述]、[作者] 和 [版本]。

步驟 2： 以滑鼠右鍵按一下專案（而非方案）。 在操作功能表上，依序選取 [**加入**] 和 [**新增專案**]。

步驟 3： 選取 [**擴充**性] 區段，然後選擇 [**命令**]。

步驟 4： 在底部的 [**名稱**] 欄位中，輸入檔案名，例如*Command.cs*。

![自訂命令](media/hello-world-vsix-command.png)

您的新命令檔會顯示在**方案總管**中。 在 [**資源**] 節點底下，您會找到與命令相關的其他檔案。 例如，如果您想要修改影像，那麼 PNG 檔案就在這裡。

## <a name="modify-the-source-code"></a>修改原始程式碼

此時，會自動產生命令和按鈕文字，而不會有太大的樂趣。 如果您想要進行變更，您可以修改 .VSCT 檔案和 CS 檔案。

* .VSCT 檔案可讓您重新命名命令，以及定義它們在 Visual Studio 命令系統中的位置。 當您流覽 .VSCT 檔案時，您會注意到說明 .VSCT 程式碼中每個區段的批註。

* CS 檔案是您可以在其中定義動作的位置，例如 click 處理常式。

::: moniker range="vs-2017"

步驟 1： 在**方案總管**中，尋找新命令的 .vsct 檔案。 在此情況下，它會被稱為*CommandPackage. .vsct*。

![命令封裝 .vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 在**方案總管**中，尋找擴充功能與套件的 .vsct 檔案。 在此情況下，它會被稱為*HelloWorldPackage. .vsct*。

::: moniker-end

步驟 2： 將 `ButtonText` 參數變更為 `Say Hello World!` 。

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

步驟 3： 返回**方案總管**並尋找*Command.cs*檔案。 在 `Execute` 方法中，將字串 `message` 從變更 `string.Format(..)` 為 `Hello World!` 。

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

請務必將您的變更儲存至每個檔案。

## <a name="run-it"></a>加以執行

您現在可以在 Visual Studio 實驗實例中執行原始程式碼。

步驟 1： 按**F5**執行 [**開始調試**] 命令。 此命令會建立您的專案，並啟動偵錯工具，啟動名為**實驗實例**的 Visual Studio 的新實例。

::: moniker range="vs-2017"

您會在 Visual Studio 標題列中看到 [**實驗實例**] 這一詞。

![實驗實例標題列](media/hello-world-exp-instance.png)

::: moniker-end

步驟 2： 在**實驗實例**的 [**工具**] 功能表上，按一下 [**說 Hello World！**]。

![最終結果](media/hello-world-final-result.png)

您應該會看到來自新自訂命令的輸出，在此案例中，畫面中央的對話方塊會提供您**Hello World！** 訊息。

## <a name="next-steps"></a>接下來的步驟

既然您已經知道使用 Visual Studio 擴充性的基本概念，您可以在這裡深入瞭解：

* [開始開發 Visual Studio 擴充](starting-to-develop-visual-studio-extensions.md)功能-範例、教學課程。 併發布您的擴充功能
* [Visual Studio 2017 SDK 的新](what-s-new-in-the-visual-studio-2017-sdk.md)功能-Visual Studio 2017 中的新擴充功能
* [Visual Studio 2019 SDK 的新](whats-new-visual-studio-2019-sdk.md)功能-Visual Studio 2019 中的新擴充功能
* 在[VISUAL STUDIO SDK 內](internals/inside-the-visual-studio-sdk.md)-瞭解 Visual Studio 擴充性的詳細資料
