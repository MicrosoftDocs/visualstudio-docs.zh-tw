---
title: Hello World 擴充功能教學課程 |Microsoft Docs
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c68ddea3f92c33056ba1dc98332755dfd3bb1b9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921034"
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

在開始之前，請確定您已安裝**Visual Studio 延伸模組開發**工作負載包括 VSIX 範本，您將需要和範例程式碼。

> [!NOTE]
> 您可以使用任何版本的 Visual Studio （Community、 Professional 或 Enterprise） 來建立 Visual Studio 擴充性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性專案

步驟 1： 從**檔案**功能表上，按一下**新的專案**。 在畫面底部，輸入您專案的名稱。

步驟 2： 從**範本**功能表上，按一下**Visual C#**，按一下 **擴充性**，然後按一下**VSIX 專案**。

![新增專案](media/hello-world-new-project.png)

您現在應該會看到 [快速入門] 頁面，以及某些範例資源。

如果您需要保留本教學課程中，然後回到該刀鋒視窗，您可以找到新的 HelloWorld 專案**起始頁**中**最近**一節。

## <a name="add-a-custom-command"></a>新增自訂命令

步驟 1： 如果您選取資訊清單時，您可以看到哪些選項已變更，例如，中繼資料、 描述和版本。

步驟 2： 以滑鼠右鍵按一下專案 （而非方案）。 在操作功能表中，按一下 **新增**，然後按一下**新項目**。

步驟 3： 選取 **擴充性**區段，然後再按一下**自訂命令**。

步驟 4： 在 **名稱**下方欄位中，為它命名，例如*Command.cs*。

![自訂命令](media/hello-world-custom-command.png)

您的新命令列在**方案總管**下方**資源**分支。 這也是您可以在其中找到與您的命令，例如如果您想要修改的映像的 PNG 和 ICO 檔案相關的其他檔案。

## <a name="modify-the-source-code"></a>修改原始程式碼

此時，您要新增的按鈕是相當泛型。 您必須修改 VSCT 檔和 CS 檔案，如果您想要進行變更。

* 您可以在此重新命名您的命令，以及定義隨處在 Visual Studio 命令系統 VSCT 檔案。 當您瀏覽 VSCT 檔案，您會發現許多加上註解的程式碼，說明每個區段的程式碼的控制項。

* CS 檔案可讓您可以在其中定義的動作，例如 click 處理常式。

步驟 1： 在 [**方案總管] 中**，尋找您的新命令的 VSCT 檔案。 在此情況下，呼叫*CommandPackage.vsct*。

![命令封裝 vsct](media/hello-world-command-package-vsct.png)

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

步驟 3： 請返回**方案總管**並尋找*Command.cs*檔案。 變更字串`message`命令`string.Format(..)`至`Hello World!`。

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

步驟 1： 按一下 **啟動**工具列中。 這會建置您的專案並開始偵錯工具，啟動 Visual Studio 呼叫的新執行個體**實驗執行個體**。

您會看到字樣**實驗執行個體**Visual Studio 標題列中。

![實驗執行個體的標題列](media/hello-world-exp-instance.png)

步驟 2： 在 **工具**功能表**實驗執行個體**，按一下  **Say Hello World ！**。

![最終結果](media/hello-world-final-result.png)

您應該會在新的自訂命令中看到輸出，在此案例中螢幕的中央的對話方塊，可讓您**Hello World ！** 訊息。

## <a name="next-steps"></a>後續步驟

既然您已經知道使用 Visual Studio 擴充性的基本概念，以下是您可以在哪裡進一步：

* [開始開發 Visual Studio 擴充功能](starting-to-develop-visual-studio-extensions.md)-範例、 教學課程。 和發佈您的延伸模組
* [在 Visual Studio 2017 SDK 最新消息](what-s-new-in-the-visual-studio-2017-sdk.md)-Visual Studio 2017 中的新擴充功能
* [在 Visual Studio SDK 內](internals/inside-the-visual-studio-sdk.md)-了解 Visual Studio 擴充性的詳細資料