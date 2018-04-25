---
title: 快速入門：使用 Visual Basic 在 Visual Studio 中建立第一個主控台應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 12/10/2017
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 39e7b9f03a5ef0a37594dad015084648eaa2bade
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>快速入門：使用 Visual Basic 在 Visual Studio 中建立第一個主控台應用程式
在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立在主控台上執行的簡單 Visual Basic 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案
首先，您將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將專案命名為 *HelloWorld*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     如果您看不到 [主控台應用程式 (.NET Core)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。

   ![按一下 [新增專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

     ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>建立應用程式
在您選取 Visual Basic 專案範本並命名專案之後，Visual Studio 會為您建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine%2A> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 。

![從範本檢視預設 Hello World 程式碼](../ide/media/vb-console-helloworld-template.png)

如果您按一下 IDE 中的 [HelloWorld] 按鈕，則可以在 [偵錯] 模式下執行程式。

  ![按一下 Hello World 按鈕，以在 [偵錯] 模式下執行程式](../ide/media/vb-console-hello-world-button.png)

當您這麼做時，主控台視窗將會在簡短顯示之後關閉。 發生原因是 `Main` 方法在其單一陳述式執行之後終止，因此應用程式結束。

### <a name="add-some-code"></a>新增一些程式碼
讓我們新增一些程式碼，來暫停應用程式，然後要求使用者輸入。

1. 緊跟在 <xref:System.Console.WriteLine%2A> 方法的呼叫後方新增下列程式碼：

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   除非您按任一鍵，否則這會暫停程式。

2. 在功能表列中，選取 [組建]  >  [組建方案]。

   這會將您的程式編譯成中繼語言 (IL)，而該語言是由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼。

## <a name="run-the-application"></a>執行應用程式
1. 按一下工具列上的 [HelloWorld] 按鈕。

   ![按一下 Hello World 按鈕，以從工具列執行程式](../ide/media/vb-console-hello-world-button.png)

2. 按任意鍵以關閉主控台視窗。

   ![顯示 Hello World 的主控台視窗，並按任意鍵繼續](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>後續步驟
恭喜您完成此快速入門！ 我們希望您更了解 Visual Basic 和 Visual Studio IDE。 若要深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [Visual Studio 中的 Visual Basic 使用者入門](tutorial-visual-basic-console.md)
