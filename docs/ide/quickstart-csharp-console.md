---
title: 使用 Visual Studio 建立您的第一個 C# 主控台應用程式
titleSuffix: ''
description: 了解如何使用 C# 在 Visual Studio 中逐步建立簡單的 Hello World 主控台應用程式。
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4ec3adbd0a8c8d6a4e37879295b040b3f91e66bd
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690175"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>快速入門：使用 Visual Studio 建立您的第一個 C# 主控台應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立在主控台上執行的簡單 C# 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，您將建立 C# 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將專案命名為 *HelloWorld*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     如果您沒有看到 [主控台應用程式 (.NET Core)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，選擇 [開啟 Visual Studio 安裝程式] 連結。

   ![從 [新增專案] 對話方塊選擇 [開啟 Visual Studio 安裝程式] 連結](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

     ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>建立應用程式

在您選取 C# 專案範本並命名專案之後，Visual Studio 會為您建立簡單的 "Hello World" 應用程式。

(它的做法是呼叫 <xref:System.Console.WriteLine%2A> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 。)

   ![從範本檢視預設 Hello World 程式碼](../ide/media/csharp-console-helloworld-template.png)

如果按下 **F5**，您可以在偵錯模式中執行程式。 不過，主控台視窗只會顯示一下子，然後就關閉。

(發生原因是 `Main` 方法在其單一陳述式執行之後終止，因此應用程式結束。)

### <a name="add-some-code"></a>新增一些程式碼

讓我們新增一些程式碼以暫停應用程式，如此主控台視窗在您按下 **ENTER** 之前都不會關閉。

1. 緊跟在 <xref:System.Console.WriteLine%2A> 方法的呼叫後方新增下列程式碼：

   ```csharp
   Console.ReadLine();
   ```

1. 請確認它在程式碼編輯器中看起來如下：

   ![新增程式碼以暫停 Hello World 應用程式](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>執行應用程式

1. 選擇工具列上的 [HelloWorld] 按鈕以在偵錯模式中執行應用程式。 (或者，您可以按下 **F5**。)

   ![選擇 [Hello World] 按鈕以從工具列執行應用程式](../ide/media/csharp-console-hello-world-button.png)

1. 在主控台視窗中檢視您的應用程式。

   ![主控台視窗顯示 Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>關閉應用程式

1. 按下 **ENTER** 以關閉主控台視窗。

1. 關閉 Visual Studio 中的 [輸出] 窗格。

   ![關閉 Visual Studio 中的 [輸出] 窗格](../ide/media/csharp-hello-world-close-output-pane.png)

1. 關閉 Visual Studio。

## <a name="next-steps"></a>後續步驟

恭喜您完成此快速入門！ 希望您已經更了解 C# 和 Visual Studio IDE。 若要深入了解，請繼續進行下列教學課程。

> [!div class="nextstepaction"]
> [開始在 Visual Studio 中使用 C# 主控台應用程式](../get-started/csharp/tutorial-console.md)
