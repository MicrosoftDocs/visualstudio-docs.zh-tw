---
title: Hello World |Microsoft 文件
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c531d8acddfebcd2656d6dca05b95244f54ec01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-your-first-extension-hello-world"></a>建立您的第一個延伸模組： Hello World

這個 Hello World 範例會引導您建立適用於 Visual Studio 的第一個延伸模組。 本教學課程會示範如何將新的命令加入 Visual Studio。

在此程序，您將學會如何：

* **[建立擴充性專案](#create-an-extensibility-project)**
* **[新增自訂命令](#add-a-custom-command)**
* **[修改原始程式碼](#modify-the-source-code)**
* **[執行此程式碼](#run-it)**

此範例中，您將使用 Visual C# 中加入自訂的功能表按鈕名為"說 Hello World ！" 這看起來像這樣：

![hello world 命令](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>必要條件

開始之前，請確定您已安裝**Visual Studio 擴充功能開發**包括 VSIX 範本，將需要和範例程式碼的工作負載。

注意： 您可以使用任何版本的 Visual Studio （Community、 Professional 或 Enterprise） 來建立 Visual Studio 擴充性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性專案

步驟 1： 從**檔案**功能表上，按一下 **新專案**。 在畫面底部，您可以輸入您的專案名稱。

步驟 2： 從**範本**功能表上，按一下  **Visual C#**，按一下 **擴充性**，然後按一下  **VSIX 專案**。

![新增專案](media/hello-world-new-project.png)

您現在應該會看到 [使用者入門] 頁面和某些範例資源。

如果您要保留此教學課程中，然後再回來時，您可以在找到新的 [HelloWorld] 專案**起始頁**中**最近**> 一節。

## <a name="add-a-custom-command"></a>新增自訂命令

步驟 1： 如果您選取資訊清單時，您可以看到哪些選項可以變更，如執行個體、 中繼資料、 說明和版本。

步驟 2： 以滑鼠右鍵按一下專案 （而非解決方案）。 在內容功能表中，按一下 **新增**，然後按一下 **使用者控制項**。

步驟 3： 請返回**擴充性**區段，然後再按一下**自訂命令**。

步驟 4： 在**名稱**底部欄位中，為它命名，例如 Command.cs。

![自訂命令](media/hello-world-custom-command.png)

您的新命令將會列在**方案總管 中**下**資源**分支。 這也是您可以在其中找到與您的命令，例如，如果您想要修改映像的 PNG 和 ICO 檔案相關的其他檔案。

## <a name="modify-the-source-code"></a>修改原始程式碼

此時，您要加入的按鈕是很泛型。 您必須修改的 VSCT 檔案和 CS 檔案，如果您想要進行變更。

* 您可以在此重新命名您的命令，以及定義位置中與 Visual Studio 命令系統 VSCT 檔案。 當您瀏覽 VSCT 檔案，您會發現許多加上註解說明每個區段的程式碼控制項的程式碼。

* CS 檔案是您可以在其中定義的動作，例如 click 處理常式。

步驟 1： 在**方案總管 中**，尋找您的新命令的 VSCT 檔案。 在此情況下，它會呼叫 CommandPackage.vsct。

![命令封裝 vsct](media/hello-world-command-package-vsct.png)

步驟 2： 變更`ButtonText`"說出 Hello World ！"的參數

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

步驟 3： 請返回**方案總管 中**尋找 Command.cs 檔案。 將字串變更為`message`命令`string.Format(..)`為"Hello World ！"

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

請務必將您的變更儲存至每個檔案。

## <a name="run-it"></a>執行此程式碼

您現在可以在 Visual Studio 的實驗執行個體中執行的原始程式碼。

步驟 1： 按一下**啟動**工具列中。 這將會建置您的專案，並開始偵錯工具，啟動 Visual Studio 呼叫的新執行個體**實驗執行個體**。

您會看到 Visual Studio 標題列中的單字 「 實驗執行個體 」。

![實驗執行個體的標題列](media/hello-world-exp-instance.png)

步驟 2： 在**工具**功能表**實驗執行個體**，按一下  **Say Hello World ！**。

![最終結果](media/hello-world-final-result.png)

您應該會在新的自訂命令，在此情況下中心對話方塊的螢幕，可讓您"Hello World ！"中看到輸出 訊息。

## <a name="next-steps"></a>後續步驟

現在，您知道使用 Visual Studio 擴充性的基本概念，以下是您可以進一步：

* [開始開發 Visual Studio 擴充功能](starting-to-develop-visual-studio-extensions.md)-範例、 教學課程。 和發行您的擴充功能。
* [What's New in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -Visual Studio 2017 中新的擴充功能
* [在 Visual Studio SDK 內](internals/inside-the-visual-studio-sdk.md)-了解 Visual Studio 擴充性的詳細資料