---
title: Hello World 擴充功能教學課程 |Microsoft Docs
description: 瞭解如何將新的命令新增為 Visual Studio 的擴充功能，包括建立專案、新增命令，以及修改原始程式碼。
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e943da6745832cbe59cfe94013650a503265636
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903290"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>教學課程-建立您的第一個延伸模組： Hello World

此 Hello World 範例會逐步引導您建立 Visual Studio 的第一個延伸模組。 本教學課程會示範如何將新的命令新增至 Visual Studio。

在此過程中，您將瞭解如何：

* **[建立擴充性專案](#create-an-extensibility-project)**
* **[新增自訂命令](#add-a-custom-command)**
* **[修改原始程式碼](#modify-the-source-code)**
* **[加以執行](#run-it)**

在此範例中，您將使用 Visual c # 來新增名為 "比方 Hello World！" 的自訂功能表按鈕 這看起來像這樣：

![Hello World 命令](media/hello-world-say-hello-world.png)

> [!NOTE]
> 本文適用于 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中](/visualstudio/mac/extending-visual-studio-mac-walkthrough)的擴充性逐步解說。

## <a name="prerequisites"></a>必要條件

開始之前，請確定您已安裝 **Visual Studio 延伸模組開發** 工作負載，其中包括您需要的 VSIX 範本和範例程式碼。

> [!NOTE]
> 您可以使用任何版本的 Visual Studio (社區、Professional 或 Enterprise) 來建立 Visual Studio 的擴充性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性專案

::: moniker range="vs-2017"

步驟 1： 從 [檔案]  功能表選取 [新增]   > [專案]  。

步驟 2： 在右上方的搜尋方塊中，輸入 "vsix"，然後選取 Visual c # **Vsix 專案**。 在對話方塊底部輸入 "HelloWorld" 作為 **名稱** ，然後選取 **[確定]**。

![新增專案](media/hello-world-new-project.png)

您現在應該會看到開始使用頁面和一些範例資源。

如果您需要離開本教學課程並回到此教學課程，您可以在 [ **開始] 頁面** 的 [ **最近** ] 區段中找到新的 HelloWorld 專案。

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 從 [檔案]  功能表選取 [新增]   > [專案]  。 搜尋 "vsix" 並選取 Visual c # **Vsix 專案** ，然後選取 [ **下一步]**。

步驟 2： 輸入 "HelloWorld" 作為 **專案名稱** ，然後選取 [ **建立**]。

![新增專案](media/hello-world-new-project-2019.png)

您現在應該會在 **方案總管** 中看到 HelloWorld 專案。

::: moniker-end

## <a name="add-a-custom-command"></a>新增自訂命令

步驟 1： 如果您選取 *extension.vsixmanifest* 資訊清單檔，您可以看到哪些選項可變更，例如 [描述]、[作者] 和 [版本]。

步驟 2： 以滑鼠右鍵按一下專案， (不是方案) 。 在內容功能表上，選取 [ **加入**]，然後選取 [ **新增專案**]。

步驟 3： 選取 [擴充性 **] 區段，然後選擇 [** **命令**]。

步驟 4： 在底部的 [ **名稱** ] 欄位中，輸入 *Command.cs* 這類的檔案名。

![自訂命令](media/hello-world-vsix-command.png)

您可以在 **方案總管** 中看到新的命令檔。 在 [ **資源** ] 節點底下，您會找到與命令相關的其他檔案。 例如，如果您想要修改影像，則 PNG 檔案位於此處。

## <a name="modify-the-source-code"></a>修改原始程式碼

此時，命令和按鈕文字會自動產生，而不是很有趣。 如果您想要進行變更，您可以修改 .VSCT 檔和 CS 檔案。

* 您可以在 .VSCT 檔案中重新命名命令，並定義它們進入 Visual Studio 命令系統的位置。 當您流覽 .VSCT 檔案時，您會看到說明 .VSCT 程式碼中每個區段的批註。

* 您可以在 CS 檔案中定義動作，例如按一下處理常式。

::: moniker range="vs-2017"

步驟 1： 在 **方案總管** 中，尋找新命令的 .vsct 檔案。 在此情況下，它會被稱為 *CommandPackage .vsct*。

![命令套件 .vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 在 **方案總管** 中，尋找您的延伸模組與套件的 .vsct 檔案。 在此情況下，它會被稱為 *HelloWorldPackage .vsct*。

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

步驟 3： 返回，以 **方案總管** 並尋找 *Command.cs* 檔案。 在 `Execute` 方法中，將字串 `message` 從變更 `string.Format(..)` 為 `Hello World!` 。

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

步驟 1： 按 **F5** 執行 [ **開始調試** ] 命令。 此命令會建立您的專案，並啟動偵錯工具，並啟動新的 Visual Studio 實例，稱為 **實驗實例**。

::: moniker range="vs-2017"

您將會在 Visual Studio 標題列中看到 [ **實驗實例** ]。

![實驗性實例標題列](media/hello-world-exp-instance.png)

::: moniker-end

步驟 2： 在 **實驗實例** 的 [**工具**] 功能表上，按一下 [**說 Hello World！**]。

![最終結果](media/hello-world-final-result.png)

您應該會看到新自訂命令的輸出，在此案例中為您提供 **Hello World** 的畫面中央對話方塊。 回應。

## <a name="next-steps"></a>下一步

現在您已瞭解使用 Visual Studio 擴充性的基本概念，以下是您可以深入瞭解的地方：

* [開始開發 Visual Studio 擴充](starting-to-develop-visual-studio-extensions.md) 功能-範例、教學課程。 併發布您的延伸模組
* [Visual Studio 2017 SDK 的新](what-s-new-in-the-visual-studio-2017-sdk.md) 功能-Visual Studio 2017 中的新擴充功能
* [Visual Studio 2019 SDK 的新](whats-new-visual-studio-2019-sdk.md) 功能-Visual Studio 2019 中的新擴充功能
* 在[VISUAL STUDIO SDK 內](internals/inside-the-visual-studio-sdk.md)-瞭解 Visual Studio 擴充性的詳細資料
