---
title: 教學課程：開始使用 Visual Basic
description: 逐步了解如何在 Visual Studio 中建立 Visual Basic 主控台應用程式。
ms.custom: vs-acquisition,  get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 8d34fef6251da95b6c3ac99430b87d853d4b5ba7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390707"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>教學課程：Visual Studio 中的 Visual Basic 使用者入門

在本教學課程中 Visual Basic (VB) ，您將使用 Visual Studio 來建立和執行一些不同的主控台應用程式，並探索 Visual Studio [整合式開發環境 (IDE) ](visual-studio-ide.md) 的一些功能。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

如果您尚未安裝 Visual Studio 2022 Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，我們將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將專案命名為 *>whatisyourname*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>新增工作負載 (選擇性)

如果您看不到 [主控台應用程式] 專案範本，則其取得方式是新增 [.NET Core 跨平台開發] 工作負載。 您可以使用下列兩種方式的其中一種來新增此工作負載，視電腦上安裝的 Visual Studio 2017 更新而定。

#### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊

1. 按一下 [新增專案] 對話方塊的左窗格中的 [開啟 Visual Studio 安裝程式] 連結。

   ![按一下 [新增專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列

1. 取消 [ **新增專案** ] 對話方塊，然後從頂端功能表列中選擇 [ **工具** > **取得工具和功能**]。

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 本教學課程中的某些螢幕擷取畫面使用深色佈景主題。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](../../ide/quickstart-personalize-the-ide.md)頁面以了解做法。

1. 開啟 Visual Studio。

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

   ![檢視 [建立新專案] 視窗](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [ **建立新專案** ] 視窗中，從 [語言] 清單中選擇 [ **Visual Basic** ]。 接下來，從 [平臺] 清單中選擇 [ **Windows** ]，然後從 [專案類型] 清單中選擇 **主控台** 。

   套用 [語言]、[平臺] 和 [專案類型] 篩選器之後，請選擇 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="選擇主控台應用程式的 Visual Basic 範本":::

   > [!NOTE]
   > 如果您沒有看到 [ **主控台應用程式** ] 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET Core 跨平台開發** 工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > 接下來，選擇 Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回至「[建立專案](#create-a-project)」程序中的步驟 2。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *WhatIsYourName*。 然後選擇 **[下一步]**。

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="在 [設定您的新專案] 視窗中，以 'WhatIsYourName' 命名您的專案":::

1. 在 [ **其他資訊** ] 視窗中，已針對您的目標架構選取 **.net Core 3.1** 。 如果沒有，請選取 [ **.Net Core 3.1**]。 然後，選擇 [ **建立**]。

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="在 [其他資訊] 視窗中，確認已選取 [.NET Core 3.1]":::

   Visual Studio 會隨即開啟您的新專案。

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>建立 "What Is Your Name" 應用程式

讓我們建立應用程式，提示您輸入您的名稱，然後顯示它與日期和時間。 方法如下：

 ::: moniker range="vs-2017"

1. 如果尚未開啟，則請開啟 *WhatIsYourName* 專案。

1. 在 `Sub Main(args As String())` 行之後的左括弧後方，以及 `End Sub` 行之前，輸入下列 Visual Basic 程式碼：

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    此程式碼取代現有的 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 和 <xref:System.Console.ReadKey%2A> 陳述式。

   ![程式碼視窗顯示 What Is Your Name 程式碼](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. 使用綠色的 [ **開始** ] 按鈕，或按 **F5** 以建立並執行您的第一個應用程式。

1. 主控台視窗開啟時，請輸入您的名稱。 主控台視窗應該類似下列螢幕擷取畫面：

   ![主控台視窗顯示 What Is Your Name、時間和日期，以及「請按任意鍵繼續」訊息](media/vb-console-what-name.png)

1. 按任意鍵關閉主控台視窗。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 *WhatIsYourName* 專案中，於 `Sub Main(args As String())` 行之後的左括弧後方，以及 `End Sub` 行之前，輸入下列 Visual Basic 程式碼：

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    此程式碼取代現有的 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 和 <xref:System.Console.ReadKey%2A> 陳述式。

   ![程式碼視窗顯示 What Is Your Name 程式碼](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. 使用綠色的 [ **開始** ] 按鈕，或按 **F5** 以建立並執行您的第一個應用程式。

1. 主控台視窗開啟時，請輸入您的名稱。 主控台視窗應該類似下列螢幕擷取畫面：

   ![主控台視窗顯示 What Is Your Name、時間和日期，以及「請按任意鍵繼續」訊息](media/vb-console-what-name.png)

1. 按任意鍵關閉主控台視窗。

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>建立 "Calculate This" 應用程式

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017]，然後從頂端功能表列 **中選擇 [** 檔案 > **新增** > **專案**]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將檔案命名為 *CalculateThis*。

1. 在 `Module Program` 行與 `End Module` 行之間輸入下列程式碼：

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   您的程式碼視窗應該類似下列螢幕擷取畫面：

   ![顯示 CalculateThis 程式碼的程式碼視窗](media/vb-codewindow-calculate-this.png)

1. 按一下 **CalculateThis** 以執行程式。 主控台視窗應該類似下列螢幕擷取畫面：

    ![顯示 CalculateThis 應用程式的主控台視窗，其中包含提示要採取的動作。](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range=">=vs-2019"

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。 

1. 在 [ **建立新專案** ] 視窗中，從 [語言] 清單中選擇 [ **Visual Basic** ]。 接下來，從 [平臺] 清單中選擇 [ **Windows** ]，然後從 [專案類型] 清單中選擇 **主控台** 。

1. 套用 [語言]、[平臺] 和 [專案類型] 篩選器之後，請選擇 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。

   然後，在 [**設定您的新專案**] 視窗中，于 [**專案名稱**] 方塊中輸入或輸入 *CalculateThis* 。 然後選擇 **[下一步]**。

1. 在 [ **其他資訊** ] 視窗中，已針對您的目標架構選取 **.net Core 3.1** 。 如果沒有，請選取 [ **.Net Core 3.1**]。 然後，選擇 [ **建立**]。

1. 在 `Module Program` 行與 `End Module` 行之間輸入下列程式碼：

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   您的程式碼視窗應該類似下列螢幕擷取畫面：

   ![顯示 CalculateThis 程式碼的程式碼視窗](media/vb-codewindow-calculate-this.png)

1. 按一下 **CalculateThis** 以執行程式。 主控台視窗應該類似下列螢幕擷取畫面：

    ![顯示 CalculateThis 應用程式的主控台視窗，其中包含提示要採取的動作。](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>常見問題集快問快答

以下提供常見問題集的快問快答，來強調幾個重要概念。

### <a name="what-is-visual-basic"></a>什麼是 Visual Basic？

Visual Basic 是一種類型安全的程式設計語言，設計成容易了解。 它是衍生自 BASIC，其表示「初學者的全方位符號式指令碼 (Beginner's All-purpose Symbolic Instruction Code)」。

### <a name="what-is-visual-studio"></a>什麼是 Visual Studio？

Visual Studio 是開發人員生產力工具的整合式開發套件。 請將它視為可用來建立程式和應用程式的程式。

### <a name="what-is-a-console-app"></a>什麼是主控台應用程式？

主控台應用程式會接受輸入，並在命令列視窗（也稱為主控台）中顯示輸出。

### <a name="what-is-net-core"></a>什麼是 .NET Core？

.NET Core 是 .NET Framework 的下一個進化步驟。 如果 .NET Framework 可讓您跨程式設計語言來共用程式碼，則 .NET Core 會新增跨平台共用程式碼的能力。 更好的是，它是開放原始碼  (.NET Framework 和 .NET Core 包含預先建置功能的程式庫以及 Common Language Runtime (CLR)，而後者作為在其中執行程式碼的虛擬機器)。

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解，請參閱下列教學課程。

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Visual Basic 和 .NET Core SDK 建置程式庫](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>另請參閱

* [Visual Basic 語言逐步解說](/dotnet/visual-basic/walkthroughs)
* [Visual Basic 語言參考](/dotnet/visual-basic/language-reference/index)
* [IntelliSense for Visual Basic 程式碼檔案](../../ide/visual-basic-specific-intellisense.md)
