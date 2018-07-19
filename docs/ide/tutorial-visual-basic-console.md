---
title: Visual Studio 中的 Visual Basic 使用者入門
ms.custom: ''
ms.date: 12/08/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: ce1c40a7031145a13eb2eebf8adaee4eba51e9fc
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280334"
---
# <a name="get-started-with-visual-basic-in-visual-studio"></a>Visual Studio 中的 Visual Basic 使用者入門

在 Visual Basic (VB) 的這個教學課程中，您將使用 Visual Studio 建立和執行一些不同的主控台應用程式，並在這麼做時探索 [Visual Studio 整合式開發環境 (IDE)](visual-studio-ide.md) 的一些功能。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="before-you-begin"></a>開始之前

以下快速常見問題集介紹一些重要概念。

### <a name="what-is-visual-basic"></a>什麼是 Visual Basic？

Visual Basic 是一種類型安全的程式設計語言，設計成容易了解。 它是衍生自 BASIC，其表示「初學者的全方位符號式指令碼 (Beginner's All-purpose Symbolic Instruction Code)」。

### <a name="what-is-visual-studio"></a>什麼是 Visual Studio？

Visual Studio 是開發人員生產力工具的整合式開發套件。 請將它視為可用來建立程式和應用程式的程式。

### <a name="what-is-a-console-app"></a>什麼是主控台應用程式？

主控台應用程式會接受輸入，並在命令列視窗 (也稱為 主控台) 中顯示輸出。

### <a name="what-is-net-core"></a>什麼是 .NET Core？

.NET Core 是 .NET Framework 的下一個進化步驟。 如果 .NET Framework 可讓您跨程式設計語言來共用程式碼，則 .NET Core 會新增跨平台共用程式碼的能力。 更好的是，它是開放原始碼  (.NET Framework 和 .NET Core 包含預先建置功能的程式庫以及 Common Language Runtime (CLR)，而後者作為在其中執行程式碼的虛擬機器)。

## <a name="start-developing"></a>開始進行開發

準備好開始進行開發了嗎？ 讓我們開始吧！

### <a name="create-a-project"></a>建立專案

首先，我們將建立 Visual Basic 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將檔案命名為 *HelloWorld*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>新增工作群組 (選擇性)

如果您看不到 [主控台應用程式] 專案範本，則其取得方式是新增 [.NET Core 跨平台開發] 工作負載。 您可以使用下列兩種方式的其中一種來新增此工作負載，視電腦上安裝的 Visual Studio 2017 更新而定。

##### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊

1. 按一下 [新增專案] 對話方塊左窗格中的 [開啟 Visual Studio 安裝程式] 連結。

  ![按一下 [新增專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列

1. 請取消 [新專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [取得工具和功能]。

2. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

## <a name="create-a-what-is-your-name-application"></a>建立 "What Is Your Name" 應用程式

讓我們建立應用程式，提示您輸入您的名稱，然後顯示它與日期和時間。 方式如下：

1. 如果尚未開啟，則請開啟 *WhatIsYourName* 專案。

2. 在 `Sub Main(args As String())` 行之後的左括弧後方，以及 `End Sub` 行之前，輸入下列 Visual Basic 程式碼：

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    此程式碼取代現有的 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 和 <xref:System.Console.ReadKey%2A> 陳述式。

 ![程式碼視窗顯示 What Is Your Name 程式碼](../ide/media/vb-codewindow-what-name.png)

3. 主控台視窗開啟時，請輸入您的名稱。 主控台視窗應該類似下列螢幕擷取畫面：

   ![主控台視窗顯示 What Is Your Name、時間和日期，以及「請按任意鍵繼續」訊息](../ide/media/vb-console-what-name.png)

5. 按任意鍵以關閉主控台視窗。

## <a name="create-a-calculate-this-application"></a>建立 "Calculate This" 應用程式

1. 開啟 Visual Studio 2017，然後從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

2. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual Basic]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將檔案命名為 *CalculateThis*。

3. 在 `Module Program` 行與 `End Module` 行之間輸入下列程式碼：

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

   ![程式碼視窗顯示 Calculate This code](../ide/media/vb-codewindow-calculate-this.png)

4. 按一下 **CalculateThis** 以執行程式。 主控台視窗應該類似下列螢幕擷取畫面：

    ![主控台視窗顯示 CaluculateThis 應用程式，其中包含提示要採取的動作。](../ide/media/vb-console-calculate-this.png)

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解 Visual Basic 和 Visual Studio IDE，請參閱下列頁面。

* [Visual Basic 指南](/dotnet/visual-basic/index)
* [Visual Basic 的新功能](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense for Visual Basic 程式碼檔案](visual-basic-specific-intellisense.md)
* [Visual Basic 語言參考](/dotnet/visual-basic/language-reference/index)
* [適合無基礎新手參加的 Visual Basic 基礎課程](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)視訊課程
