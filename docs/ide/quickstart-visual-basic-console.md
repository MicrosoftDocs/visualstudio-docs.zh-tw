---
title: 使用 Visual Basic 建立您的第一個主控台應用程式
description: 了解如何使用 Visual Basic 在 Visual Studio 中逐步建立簡單的 Hello World 主控台應用程式。
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579506"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>快速入門：使用 Visual Basic 在 Visual Studio 中建立第一個主控台應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立在主控台上執行的簡單 Visual Basic 應用程式。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，您將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中 **，選擇 [** 檔案] > [**新增**>**專案**]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將專案命名為 *HelloWorld*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     如果您看不到 [主控台應用程式 (.NET Core)] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。

   ![按一下 [新增專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

     ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> 本快速入門中的某些螢幕擷取畫面使用深色佈景主題。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](quickstart-personalize-the-ide.md)頁面以了解做法。

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [建立新專案]。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案] 視窗的搜尋方塊中輸入或鍵入 ASP.NET。 接下來，從語言清單中選擇 **Visual Basic**，然後從平台清單中選擇 **Windows**。 

   在您套用語言和平台的篩選條件之後，請選擇 [主控台應用程式 (.NET Core)] 範本，然後選擇 [下一步]。

   ![選擇主控台應用程式 (.NET Framework) 的 Visual Basic 專案範本](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > 如果您未看到 [主控台應用程式 (.NET Core)] 範本，您可以從 [建立新專案] 視窗中安裝。 在 [找不到你要尋找的項目嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中 [找不到您要找的資料嗎?] 訊息的 [安裝更多的工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET Core 跨平台開發**工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > 接著，選擇Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回這個「[建立專案](#create-a-project)」程序中的第 2 步。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 **WhatIsYourName**。 接著，選擇 [建立]。

   ![在 [設定您的新專案] 視窗中，以 'WhatIsYourName' 命名您的專案](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio 會開啟您的新專案。

::: moniker-end

## <a name="create-the-application"></a>建立應用程式

在您選取 Visual Basic 專案範本並命名專案之後，Visual Studio 會為您建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine%2A> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 訊息。

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

2. 在功能表列中，選取 [組建] >  [組建方案]。

   這會將您的程式編譯成中繼語言 (IL)，而該語言是由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼。

## <a name="run-the-application"></a>執行應用程式

1. 按一下工具列上的 [HelloWorld] 按鈕。

   ![按一下 Hello World 按鈕，以從工具列執行程式](../ide/media/vb-console-hello-world-button.png)

2. 按任意鍵關閉主控台視窗。

   ![顯示 Hello World 的主控台視窗，並按任意鍵繼續](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>後續步驟

恭喜您完成此快速入門！ 我們希望您更了解 Visual Basic 和 Visual Studio IDE。 若要深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [Visual Studio 中的 Visual Basic 使用者入門](../get-started/visual-basic/tutorial-console.md)
