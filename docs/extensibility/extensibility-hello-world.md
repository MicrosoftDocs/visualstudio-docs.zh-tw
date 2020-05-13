---
title: 你好世界擴展教程 |微軟文件
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711655"
---
# <a name="create-your-first-extension-hello-world"></a>建立您的第一個擴展:你好世界

此 Hello World 示例引導您為 Visual Studio 創建第一個擴展。 本教程演示如何向 Visual Studio 添加新命令。

在此過程中,您將學習如何:

* **[建立擴充性項目](#create-an-extensibility-project)**
* **[新增自訂指令](#add-a-custom-command)**
* **[變更原始碼](#modify-the-source-code)**
* **[加以執行](#run-it)**

此範例中,您將使用 Visual C# 添加名為「問好世界! 如下所示:

![你好世界命令](media/hello-world-say-hello-world.png)

> [!NOTE]
> 本文適用於 Windows 上的可視化工作室。 有關 Mac 的視覺化工作室,請參閱[Mac 視覺工作室中的擴充性演練](/visualstudio/mac/extending-visual-studio-mac-walkthrough)。

## <a name="prerequisites"></a>Prerequisites

在開始之前,請確保已安裝**Visual Studio 擴展開發**工作負荷,其中包括您需要的 VSIX 範本和範例代碼。

> [!NOTE]
> 您可以使用任何版本的視覺工作室(社區、專業版或企業版)創建可視化工作室擴展性專案。

## <a name="create-an-extensibility-project"></a>建立擴充性項目

::: moniker range="vs-2017"

步驟 1： 從 [檔案]**** 功能表選取 [新增]**** > [專案]****。

步驟 2： 在右上角的搜尋框中,鍵入「vsix」並選擇 Visual C# **VSIX 專案**。 在對話框底部輸入 **「HelloWorld」,** 然後選擇 **「確定**」。

![新增專案](media/hello-world-new-project.png)

現在,您應該會看到"入門"頁和一些示例資源。

如果您需要離開本教程並返回本教程,您可以在 **"最近**"部分的 **"開始頁面"** 中找到您的新 HelloWorld 專案。

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 從 [檔案]**** 功能表選取 [新增]**** > [專案]****。 搜尋"vsix",然後選擇可視化 C# **VSIX 專案**,然後**選擇"下一個**"。

步驟 2： 為**專案名稱**輸入"HelloWorld",然後選擇 **"創建**"。

![新增專案](media/hello-world-new-project-2019.png)

現在,您應該在**解決方案資源管理器**中看到 HelloWorld 專案。

::: moniker-end

## <a name="add-a-custom-command"></a>新增自訂指令

步驟 1： 如果選擇 *.vsix清單清單*檔,您可以看到哪些選項是可更改的,例如說明、作者和版本。

步驟 2： 右鍵單擊專案(不是解決方案)。 在上下文選單上,選擇 **「添加**」,然後**選擇「新建項**」。

步驟 3： 選擇「**擴充性**」 部份, 然後選擇**指令**。

步驟 4： 在底部的**名稱「 欄**位中,輸入檔案名稱」,如*Command.cs*。

![自訂指令](media/hello-world-vsix-command.png)

您的新命令檔在**解決方案資源管理器**中可見。 在 **「資源」** 節點下,您將找到與您的指令相關的其他檔。 例如,如果要修改圖像,PNG 檔就在這裡。

## <a name="modify-the-source-code"></a>變更原始碼

此時,命令和按鈕文本是自動生成的,不是很有趣。 如果要進行更改,可以修改 VSCT 檔和 CS 檔。

* VSCT 檔案是您可以重新命名命令以及定義命令在 Visual Studio 命令系統中的位置的位置。 在瀏覽 VSCT 檔時,您會注意到解釋 VSCT 代碼的每個部分控制項的註解。

* CS 檔案是您可以定義操作(如單擊處理程式)的位置。

::: moniker range="vs-2017"

步驟 1： 在**解決方案資源管理員**中,尋找新命令的 VSCT 檔。 在這種情況下,它將稱為*命令包.*

![命令套件 vct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

步驟 1： 在**解決方案資源管理員**中,尋找副檔名 VS 套件的 VSCT 檔案。 在這種情況下,它將被稱為*HelloWorldPackage.vsct。*

::: moniker-end

步驟 2： 將`ButtonText`參數變更`Say Hello World!`為 。

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

步驟 3： 返回**解決方案資源管理員**並找到*Command.cs*檔。 在`Execute`方法中,將字串`message`從`string.Format(..)``Hello World!`變更為 。

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

請確保將更改儲存到每個檔中。

## <a name="run-it"></a>加以執行

您現在可以在可視化工作室實驗實例中運行原始程式碼。

步驟 1： 按**F5**以運行 **「開始調試」** 命令。 此命令生成項目並啟動除錯器,啟動稱為**實驗實例**的 Visual Studio 的新實例。

::: moniker range="vs-2017"

您將在"視覺工作室"標題列中看到"**實驗實例**"一詞。

![實驗實例標題列](media/hello-world-exp-instance.png)

::: moniker-end

步驟 2： 在**實驗實例****的工具**功能表上,單擊 **"打你好世界!"**

![最終結果](media/hello-world-final-result.png)

您應該看到來自新自定義命令的輸出,在這種情況下,螢幕中心的對話框將為您提供**Hello World!** 訊息。

## <a name="next-steps"></a>後續步驟

現在,您已經瞭解了使用 Visual Studio 可擴充性的基礎知識,您可以在此處瞭解詳細資訊:

* [開始開發可視化工作室擴展](starting-to-develop-visual-studio-extensions.md)- 示例,教程。 並發布您的延伸
* [視覺工作室 2017 SDK 中的新增功能](what-s-new-in-the-visual-studio-2017-sdk.md)- Visual Studio 2017 中新的擴充功能
* [視覺工作室 2019 SDK 中的新增功能](whats-new-visual-studio-2019-sdk.md)- Visual Studio 2019 中新的擴充功能
* [在視覺化工作室 SDK 中](internals/inside-the-visual-studio-sdk.md)- 瞭解視覺化工作室可擴充性的詳細資訊
