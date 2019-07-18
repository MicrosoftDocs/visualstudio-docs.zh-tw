---
title: Hello World 擴充功能教學課程 |Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c3bbafcf138c60b65940bcee73c74f56cf6e2fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342867"
---
# <a name="create-your-first-extension-hello-world"></a>建立您的第一個延伸模組：Hello World

這個 Hello World 範例會引導您完成適用於 Visual Studio 建立您的第一個延伸模組。 本教學課程會示範如何將新的命令新增至 Visual Studio。

在過程中，您將了解如何：

* **[建立擴充性專案](#create-an-extensibility-project)**
* **[新增自訂命令](#add-a-custom-command)**
* **[修改原始程式碼](#modify-the-source-code)**
* **[執行它](#run-it)**

此範例中，您將使用 Visual C# 中新增自訂的功能表按鈕名為 「 顯示 Hello World ！ 」 看起來像這樣：

![Hello World 命令](media/hello-world-say-hello-world.png)

> [!NOTE]
> 這篇文章適用於在 Windows 上的 Visual Studio。 Visual Studio for Mac，請參閱 <<c0> [ 擴充性的逐步解說在 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough)。

## <a name="prerequisites"></a>必要條件

在開始之前，請確定您已安裝**Visual Studio 延伸模組開發**工作負載，包括您將需要和範例程式碼中的 [VSIX] 範本。

> [!NOTE]
> 您可以使用任何版本的 Visual Studio （Community、 Professional 或 Enterprise） 來建立 Visual Studio 擴充性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性專案

::: moniker range="vs-2017"

步驟 1： 從 [檔案]  功能表選取 [新增]   > [專案]  。

步驟 2： 在右上角的 [搜尋] 方塊中，輸入 「 vsix 」 並選取視覺效果C# **VSIX 專案**。 輸入"HelloWorld"**名稱**底部的對話方塊，然後選取**確定**。

![新增專案](media/hello-world-new-project.png)

您現在應該會看到 [快速入門] 頁面，以及某些範例資源。

如果您需要保留本教學課程中，然後回到該刀鋒視窗，您可以找到新的 HelloWorld 專案**起始頁**中**最近**一節。

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 從 [檔案]  功能表選取 [新增]   > [專案]  。 搜尋"vsix 」 並選取視覺效果C# **VSIX 專案**，然後**下一步**。

步驟 2： 輸入"HelloWorld"**專案名稱**，然後選取**建立**。

![新增專案](media/hello-world-new-project-2019.png)

您現在應該會看到中的 HelloWorld 專案**方案總管 中**。

::: moniker-end

## <a name="add-a-custom-command"></a>新增自訂命令

步驟 1： 如果您選取 *.vsixmanifest*資訊清單檔案中，您可以看到哪些選項已變更，例如描述、 作者和版本。

步驟 2： 以滑鼠右鍵按一下專案 （而非方案）。 在操作功能表中，選取**新增**，然後**新項目**。

步驟 3： 選取 **擴充性**區段，然後再選擇**自訂命令**。

步驟 4： 在 **名稱**下方欄位中，輸入檔案名稱，例如*Command.cs*。

![自訂命令](media/hello-world-custom-command.png)

新的命令檔會顯示在**方案總管 中**。 底下**資源** 節點，您會發現與命令相關的其他檔案。 例如，如果您想要修改的映像，該 PNG 檔案隆重上市。

## <a name="modify-the-source-code"></a>修改原始程式碼

此時，命令和按鈕文字會自動產生並不是很有趣。 如果您想要進行變更，您可以修改的 VSCT 檔和 CS 檔案。

* 您可以在此重新命名您的命令，以及定義隨處在 Visual Studio 命令系統 VSCT 檔案。 當您瀏覽 VSCT 檔案，您會發現說明哪些的 VSCT 程式碼控制項的每個區段的註解。

* CS 檔案可讓您可以在其中定義的動作，例如 click 處理常式。

::: moniker range="vs-2017"

步驟 1： 在 [**方案總管] 中**，尋找您的新命令的 VSCT 檔案。 在此情況下，呼叫*CommandPackage.vsct*。

![命令封裝 vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 在 [**方案總管] 中**，尋找擴充功能與套件之 VSCT 檔。 在此情況下，呼叫*HelloWorldPackage.vsct*。

::: moniker-end

步驟 2： 變更`ButtonText`參數來`Say Hello World!`。

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

步驟 3： 請返回**方案總管**並尋找*Command.cs*檔案。 在 `Execute`方法，將字串變更為`message`從`string.Format(..)`來`Hello World!`。

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

請務必將變更儲存至每個檔案。

## <a name="run-it"></a>執行它

您現在可以在 Visual Studio 的實驗執行個體中執行的原始程式碼。

步驟 1： 按下**F5**來執行**開始偵錯**命令。 此命令會建置您的專案，並開始偵錯工具，啟動 Visual Studio 呼叫的新執行個體**實驗執行個體**。

::: moniker range="vs-2017"

您會看到字樣**實驗執行個體**Visual Studio 標題列中。

![實驗執行個體的標題列](media/hello-world-exp-instance.png)

::: moniker-end

步驟 2： 在 **工具**功能表**實驗執行個體**，按一下  **Say Hello World ！** 。

![最終結果](media/hello-world-final-result.png)

您應該會在新的自訂命令中看到輸出，在此案例中螢幕的中央的對話方塊，可讓您**Hello World ！** 訊息。

## <a name="next-steps"></a>後續步驟

既然您已經知道使用 Visual Studio 擴充性的基本概念，以下是您可以在哪裡進一步：

* [開始開發 Visual Studio 擴充功能](starting-to-develop-visual-studio-extensions.md)-範例、 教學課程。 和發佈您的延伸模組
* [在 Visual Studio 2017 SDK 最新消息](what-s-new-in-the-visual-studio-2017-sdk.md)-Visual Studio 2017 中的新擴充功能
* [在 Visual Studio 2019 SDK 最新消息](whats-new-visual-studio-2019-sdk.md)-新的擴充性功能，在 Visual Studio 2019
* [在 Visual Studio SDK 內](internals/inside-the-visual-studio-sdk.md)-了解 Visual Studio 擴充性的詳細資料