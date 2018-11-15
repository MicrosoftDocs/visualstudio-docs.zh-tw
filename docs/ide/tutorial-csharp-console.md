---
title: 開始在 Visual Studio 中使用 C# 主控台應用程式
description: 了解如何逐步在 Visual Studio 中建立 C# 主控台應用程式。
ms.custom: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 3450572e4cf4959530599c5eea9efb3168485b58
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244368"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>教學課程：開始在 Visual Studio 中使用 C# 主控台應用程式

在 C# 的這個教學課程中，您將使用 Visual Studio 建立並執行主控台應用程式，並在這樣做的同時探索 [Visual Studio 整合式開發環境 (IDE)](visual-studio-ide.md) 的一些功能。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，我們要建立 C# 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 接著，將檔案命名為 *Calculator*。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>新增工作群組 (選擇性)

如果您看不到 [主控台應用程式] 專案範本，則其取得方式是新增 [.NET Core 跨平台開發] 工作負載。 您可以使用下列兩種方式的其中一種來新增此工作負載，視電腦上安裝的 Visual Studio 2017 更新而定。

#### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊

1. 選擇 [新增專案] 對話方塊左窗格中的 [開啟 Visual Studio 安裝程式] 連結。

   ![從 [新增專案] 對話方塊選擇 [開啟 Visual Studio 安裝程式] 連結](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列

1. 請取消 [新專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [取得工具和功能]。

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

## <a name="create-a-c-console-calculator-app"></a>建立「C# 主控台 Calculator」應用程式

1. 在您建立 **C# 主控台應用程式**之後，將下列程式碼輸入或貼入程式碼編輯器中：

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   出現在 `static void Main(string[] args)` 後面的程式碼看起來應該如下列螢幕擷取畫面：

   ![顯示 C# 主控台 Calculator 的程式碼編輯器](../ide/media/csharp-console-calculator-code.png)

1. 選擇 [Calculator] 來執行您的程式 (或按 **F5**)。

   ![選擇 [Calculator] 按鈕以從工具列執行應用程式](../ide/media/csharp-console-calculator-button.png)

1. 在主控台視窗中檢視您的應用程式。 當您遵循提示操作時，您的應用程式看起來應該類似下列螢幕擷取畫面：

    ![主控台視窗顯示 Caluculate 應用程式，其中包含要採取之動作的提示。](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>關閉應用程式

1. 按任意鍵來關閉計算機應用程式。

1. 關閉 Visual Studio 中的 [輸出] 窗格。

   ![關閉 Visual Studio 中的 [輸出] 窗格](../ide/media/csharp-calculator-close-output-pane.png)

1. 關閉 Visual Studio。

## <a name="quick-answers-faq"></a>常見問題集快問快答

以下提供常見問題集的快問快答，來強調幾個重要概念。

### <a name="what-is-c"></a>什麼是 C#?

C# 是在 NET Framework 與 .NET Core 上執行的型別安全程式設計語言。 使用 C#，您可以建立 Windows 應用程式、主從式應用程式、資料庫應用程式、XML Web Service、分散式元件等等。

### <a name="what-is-visual-studio"></a>什麼是 Visual Studio？

Visual Studio 是開發人員生產力工具的整合式開發套件。 請將它視為可用來建立程式和應用程式的程式。

### <a name="what-is-a-console-app"></a>什麼是主控台應用程式？

主控台應用程式會接受輸入，並在命令列視窗 (也稱為 主控台) 中顯示輸出。

### <a name="what-is-net-core"></a>什麼是 .NET Core？

.NET Core 是 .NET Framework 的下一個進化步驟。 如果 .NET Framework 可讓您跨程式設計語言來共用程式碼，則 .NET Core 會新增跨平台共用程式碼的能力。 更好的是，它是開放原始碼 

(.NET Framework 與 .NET Core 都包含預先建置功能的程式庫。 它們也包含通用語言執行平台 (CLR)，它會作為執行您程式碼的虛擬機器。)

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [C# 教學課程](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>另請參閱

* [適合無基礎新手參加的 C# 基礎影片課程](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
