---
title: '教學課程：建立簡單的 c # 主控台應用程式'
description: 了解如何逐步在 Visual Studio 中建立 C# 主控台應用程式。
ms.custom: seodec18, get-started
ms.date: 02/18/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 484cb82a3659e306bd4c6bd14a3133c4677160db
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833334"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>教學課程：在 Visual Studio 中建立簡單的 c # 主控台應用程式

在 C# 的這個教學課程中，您將使用 Visual Studio 建立並執行主控台應用程式，並在這樣做的同時探索 Visual Studio 整合式開發環境 (IDE) 的一些功能。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，我們將建立 C# 應用程式專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。
    (或者，按下 **Ctrl** + **Shift** + **N**) 。

3. 在 [新增專案] 對話方塊的左窗格中，展開 C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [主控台應用程式 (.NET Core)]。 然後將檔案命名為 **_計算機_* _。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的主控台應用程式 (.NET Core) 專案範本](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>新增工作負載 (選擇性)

如果您沒有看到 _ *主控台應用程式 ( .Net core)** 專案範本，您可以藉由新增 **.net core 跨平臺開發** 工作負載來取得它。 方法如下。

#### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊

1. 選擇 [新增專案] 對話方塊左窗格中的 [開啟 Visual Studio 安裝程式] 連結。

   ![從 [新增專案] 對話方塊選擇 [開啟 Visual Studio 安裝程式] 連結](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列

1. 請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具]**[取得工具和功能]** > 。

1. Visual Studio 安裝程式即會啟動。 選擇 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

   ![檢視 [建立新專案] 視窗](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案] 視窗的搜尋方塊中輸入或鍵入 ASP.NET。 接下來，從語言清單中選擇 **C#**，然後從平台清單中選擇 **Windows**。 

   在您套用語言和平台的篩選條件之後，請選擇 [主控台應用程式 (.NET Core)] 範本，然後選擇 [下一步]。

   ![選擇主控台應用程式 (.NET Framework) 的 C# 專案範本](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > 如果您未看到 [主控台應用程式 (.NET Core)] 範本，您可以從 [建立新專案] 視窗中安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 接下來，在 Visual Studio 安裝程式中選擇 **.NET Core 跨平台開發** 工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](./media/dot-net-core-xplat-dev-workload.png)
   >
   > 接下來，選擇 Visual Studio 安裝程式中的 [修改] 按鈕。 系統可能會提示您儲存工作，若收到提示，請依提示執行。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回至「[建立專案](#create-a-project)」程序中的步驟 2。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *Calculator*。 然後，選擇 [ **建立**]。

   ![在 [設定您的新專案] 視窗中，以 'Calculator' 命名您的專案](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio 會隨即開啟您的新專案，其中包含預設 "Hello World" 程式碼。
   
::: moniker-end

## <a name="create-the-app"></a>建立應用程式

首先，我們將探索一些以 C# 撰寫的基本整數運算。 然後，我們將新增程式碼來建立基本的計算機。 然後，我們會對應用程式進行偵錯以找出錯誤，將其修正。 最後，我們會精簡程式碼，讓其更有效率。

### <a name="explore-integer-math"></a>探索整數運算

讓我們開始使用一些以 C# 撰寫的基本整數運算。

1. 在程式碼編輯器中，刪除預設 "Hello World" 程式碼。

    ![從新的計算機應用程式中刪除預設 Hello World 程式碼](./media/csharp-console-calculator-deletehelloworld.png)

   具體來說，刪除 `Console.WriteLine("Hello World!");` 一行。

1. 鍵入下列程式碼來取代：

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    請注意，當您這麼做時，Visual Studio 中的 IntelliSense 功能會提供您自動完成項目的選項。

    > [!NOTE]
    > 下列動畫不是為了複製上述程式碼。 其目的只是為了說明自動完成功能的運作方式。

    ![顯示 Visual Studio IDE 中 IntelliSense 自動完成功能的整數數學代碼動畫](./media/integer-math-intellisense.gif)

1. 選擇 [**計算機**] 旁的綠色 [**開始**] 按鈕，以建立並執行您的程式，或按下 **F5**。

   ![選擇 [Calculator] 按鈕以從工具列執行應用程式](./media/csharp-console-calculator-button.png)

   主控台視窗會隨即開啟並顯示 42 + 119 的總和，也就是 **161**。

    ![顯示整數數學結果的主控台視窗](./media/csharp-console-integer-math.png)

1. (選擇性)，您可以變更運算子來變更結果。 例如，您可以將 `int c = a + b;`程式碼行中的 `+` 運算子變更為 `-` 進行相減、變更為 `*` 進行相乘，或變更為 `/` 進行相除。 在您執行程式時，結果也會變更。

1. 關閉主控台視窗。

### <a name="add-code-to-create-a-calculator"></a>新增程式碼來建立計算機

讓我們繼續將一組更複雜的計算機程式碼新增至專案。

1. 刪除您在程式碼編輯器中看到的所有程式碼。

1. 在程式碼編輯器中輸入或貼上下列新程式碼：

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
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
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. 選擇 [Calculator] 來執行您的程式 (或按 **F5**)。

   ![選擇 [Calculator] 按鈕以從工具列執行應用程式](./media/csharp-console-calculator-button.png)

   主控台視窗隨即開啟。

1. 在主控台視窗中檢視您的應用程式，然後遵循提示來新增數字 **42** 和 **119**。

   您的應用程式看起來應該類似下列螢幕擷取畫面：

    ![主控台視窗顯示計算機應用程式，並包含要採取之動作的提示](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>將功能新增至計算機

我們將調校程式碼來新增進一步的功能。

### <a name="add-decimals"></a>新增小數

目前，計算機應用程式會接受並傳回整數。 但如果我們新增可允許小數的程式碼，會讓其更精確。

如下列螢幕擷取畫面所示，如果您執行應用程式，將數字 42 除以數字 119，結果會是 0 (零)，並不正確。

![主控台視窗顯示計算機應用程式不會在結果中傳回小數](./media/csharp-console-calculator-nodecimal.png)

讓我們修正程式碼來處理小數。

1. 按 **Ctrl**  +  **H** 以開啟 [**尋找和取代**] 控制項。

1. 將 `int` 變數的每個執行個體變更為 `float`。

   請確認您已在 [尋找和取代] 控制項中切換 [大小寫須相符] (**ALT**+**C**) 和 [全字相符] (**ALT**+**W**)。

    ![顯示如何將 int 變數變更為 float 的 [尋找和取代] 控制項動畫](./media/find-replace-control-animation.gif)

1. 再次執行您的計算機應用程式，將數字 **42** 除以數字 **119**。

   您會看到應用程式現在會傳回小數，而不是零。

    ![主控台視窗顯示計算機應用程式現在會在結果中傳回小數](./media/csharp-console-calculator-decimal.png)

不過，應用程式僅會產生小數結果。 讓我們進一步調校程式碼，讓應用程式也可以計算小數。

1. 您可以使用 [**尋找和取代**] 控制項 (**Ctrl**  +  **H**) 將變數的每個實例變更 `float` 為 `double` ，並將方法的每個實例變更 `Convert.ToInt32` 為 `Convert.ToDouble` 。

1. 執行您的計算機應用程式，將數字 **42.5** 除以數字 **119.75**。

   您會看到應用程式現在接受小數值，並會在結果中傳回較長的小數數字。

    ![主控台視窗顯示計算機應用程式現在接受小數數字並在結果中傳回小數數字](./media/csharp-console-calculator-usedecimals.png)

    (我們將在[修改程式碼](#revise-the-code)一節中修正小數位數數字。)

## <a name="debug-the-app"></a>偵錯應用程式

我們已改善基本計算機應用程式，但還不具備處理例外狀況的保險方式，例如使用者輸入錯誤。

例如，如果您嘗試將數位零除，或在應用程式需要數位字元時輸入英數位元 (或反之亦然) ，則應用程式可能會停止運作、傳回錯誤或傳回非預期的非數值結果。

讓我們逐步解說一些常見的使用者輸入錯誤，如果出現在偵錯工具中，請在偵錯工具中找出這些錯誤，然後在程式碼中加以修正。

> [!TIP]
> 如需偵錯工具及其運作方式的詳細資訊，請參閱 [Visual Studio 偵錯工具初探](../../debugger/debugger-feature-tour.md)頁面。

### <a name="fix-the-divide-by-zero-error"></a>修正「除以零」錯誤

當您嘗試將數位零除時，主控台應用程式可能會凍結，然後顯示程式碼編輯器中的錯誤。

   ![Visual Studio 程式碼編輯器的螢幕擷取畫面，其中顯示以黃色醒目提示的行，以及「嘗試零除的例外狀況未處理錯誤」。](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> 有時候，應用程式不會凍結，偵錯工具不會顯示零除的錯誤。 相反地，應用程式可能會傳回非預期的非數值結果，例如無限符號。 下列程式碼修正仍適用。

讓我們變更程式碼來處理此錯誤。

1. 刪除直接出現在 `case "d":` 和指出 `// Wait for the user to respond before closing` 之註解間的程式碼。

1. 使用下列程式碼將其取代：

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   新增程式碼後，具有 `switch` 陳述式的區段看起來會類似下列螢幕擷取畫面：

   ![Visual Studio 程式碼編輯器中經修改的「切換」區段](./media/csharp-console-calculator-switch-code.png)

現在，當您將任何數字除以零時，應用程式會要求輸入其他數字。 更好的：它不會停止詢問，直到您提供零以外的數位為止。

   ![Visual Studio 程式碼編輯器的螢幕擷取畫面，其中顯示 switch 語句的程式碼，並檢查是否已加入非零除數的專案。](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>修正「格式」錯誤

如果應用程式僅接受數字字元，而您輸入了英文字元 (反之亦然)，則主控台應用程式會凍結。 Visual Studio 接著會顯示程式碼編輯器中的錯誤。

   ![Visual Studio 程式碼編輯器顯示格式錯誤](./media/csharp-console-calculator-format-error.png)

若要修正此錯誤，我們必須重構先前輸入的程式碼。

#### <a name="revise-the-code"></a>修改程式碼

我們將應用程式分為兩類：`Calculator` 和 `Program`，而不依賴 `program` 類別來處理所有程式碼。

`Calculator` 類別會處理大量計算工作，`Program` 類別會處理使用者介面和錯誤擷取工作。

現在就開始吧。

1. 刪除 `Calculator` 命名空間中左右大括弧之間的所有內容：

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. 接下來，新增 `Calculator` 類別，如下所示：

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. 然後，新增 `Program` 類別，如下所示：

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. 選擇 [Calculator] 來執行您的程式 (或按 **F5**)。

1. 遵循提示，將數字 **42** 除以數字 **119**。 您的應用程式看起來應該類似下列螢幕擷取畫面：

    ![主控台視窗顯示重構的應用程式，包含要採取那些動作和處理不正確輸入的提示](./media/csharp-console-calculator-refactored.png)

    請注意，在您關閉主控台應用程式前，您可以選擇輸入其他方程式。 此外，我們也減少了結果中的小數位數。

## <a name="close-the-app"></a>關閉應用程式

1. 如果您尚未這麼做，請關閉計算機應用程式。

1. 關閉 Visual Studio 中的 [ **輸出** ] 窗格。

   ![關閉 Visual Studio 中的 [輸出] 窗格](./media/csharp-calculator-close-output-pane.png)

1. 在 Visual Studio 中，按 **Ctrl** + **S** 以儲存您的應用程式。

1. 關閉 Visual Studio。

## <a name="code-complete"></a>程式碼完成

在本教學課程中，我們對計算機應用程式進行了許多變更。 應用程式現在會更有效率處理運算資源，並處理大部分的使用者輸入錯誤。

以下是完整程式碼總整理：

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>後續步驟

:::moniker range="vs-2017"

繼續進行更多教學課程：

> [!div class="nextstepaction"]
> [C# 教學課程](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [體驗 Visual Studio IDE](../visual-studio-ide.md)

:::moniker-end

:::moniker range="vs-2019"

繼續進行本教學課程的第二部分：

> [!div class="nextstepaction"]
> [繼續進行第2部分](tutorial-console-part-2.md)
:::moniker-end

## <a name="see-also"></a>請參閱

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [了解如何在 Visual Studio 中偵錯 C# 程式碼](tutorial-debugger.md)
