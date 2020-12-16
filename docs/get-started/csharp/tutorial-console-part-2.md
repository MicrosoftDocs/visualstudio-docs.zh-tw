---
title: '教學課程：擴充簡單的 c # 主控台應用程式'
description: '逐步瞭解如何在 Visual Studio 中開發 c # 主控台應用程式。'
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 55b1e30d214ff85bfc1b7e9c00ebff7e76a95f12
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527878"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>教學課程：擴充簡單的 c # 主控台應用程式

在本教學課程中，您將瞭解如何使用 Visual Studio 來延伸您在第一個部分中建立的主控台應用程式。 您將瞭解每日開發需要 Visual Studio 的一些功能，例如管理多個專案，以及參考協力廠商套件。

如果您剛完成本系列的 [第一個部分](tutorial-console.md) ，則您已經有計算機主控台應用程式。  若要略過第1部分，您可以從 GitHub 存放庫開啟專案開始。 C # 計算機應用程式位於 vs 教學課程 [範例](https://github.com/MicrosoftDocs/vs-tutorial-samples)存放庫中，因此您可以直接依照 [教學課程：從存放庫開啟專案](../tutorial-open-project-from-repo.md) 以開始使用中的步驟進行。

## <a name="add-a-new-project"></a>新增專案

真實世界的程式碼牽涉到許多專案在解決方案中一起運作。 現在，讓我們將另一個專案新增至計算機應用程式。 這會是提供一些計算機函數的類別庫。

1. 在 Visual Studio 中，您可以使用最上層的 **功能表命令檔**[  >  **加入**  >  **新的專案**] 來加入新的專案，但您也可以用滑鼠右鍵按一下現有的專案名稱， (稱為「專案節點」 ) 然後開啟專案的快捷方式功能表 (或內容功能表) 。 此快捷方式功能表包含許多方法，可將功能新增至您的專案。 因此，以滑鼠右鍵按一下 **方案總管** 中的專案節點，然後選擇 [**加入**  >  **新專案**]。

1. 選擇 c # 專案範本 **類別庫 ( .NET Standard)**。

   ![類別庫專案範本選取專案的螢幕擷取畫面](media/vs-2019/calculator2-add-project-dark.png)

1. 輸入專案名稱 **CalculatorLibrary**，然後選擇 [ **建立**]。 Visual Studio 會建立新的專案，並將其加入至方案。

   ![已新增 CalculatorLibrary 類別庫專案方案總管的螢幕擷取畫面](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. 請重新命名 **CalculatorLibrary.cs** 檔案，而不是 *Class1.cs*。 您可以按一下 **方案總管** 中的名稱來重新命名，或按一下滑鼠右鍵並選擇 [ **重新命名**]，或按 **F2** 鍵。

   如果您想要重新命名檔案中的任何參考，可能會被詢問您 `Class1` 。 這並不重要，因為您將會在未來的步驟中取代程式碼。

1. 我們現在必須加入專案參考，讓第一個專案可以使用新類別庫所公開的 Api。  以滑鼠右鍵按一下第一個專案中的 [ **參考** ] 節點，然後選擇 [ **加入專案參考**]。

   ![[新增專案參考] 功能表項目的螢幕擷取畫面](media/vs-2019/calculator2-add-project-reference-dark.png)

   [參考管理員] 對話方塊隨即顯示。 這個對話方塊可讓您加入其他專案的參考，以及您的專案所需的元件和 COM Dll。

   ![[參考管理員] 對話方塊的螢幕擷取畫面](media/vs-2019/calculator2-ref-manager-dark.png)

1. 在 [ **參考管理員** ] 對話方塊中，選取 **CalculatorLibrary** 專案的核取方塊，然後選擇 **[確定]**。  專案參考會出現在 **方案總管** 的 [**專案**] 節點底下。

   ![專案參考方案總管的螢幕擷取畫面](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. 在 *Program.cs* 中，選取 `Calculator` 類別及其所有程式碼，然後按下 **CTRL + X** 以將它從 Program.cs 剪下。 然後在 **CalculatorLibrary** 的 *CalculatorLibrary.cs* 中，將程式碼貼到 `CalculatorLibrary` 命名空間中。 然後，讓計算機類別 `public` 在程式庫外部公開。 *CalculatorLibrary.cs* 中的程式碼現在應該類似下列程式碼：

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. 第一個專案有參考，但您會看到 Dooperation-add-0.invoke 呼叫無法解析的錯誤。 這是因為 CalculatorLibrary 是在不同的命名空間中，因此請新增 `CalculatorLibrary` 完整參考的命名空間。

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   請嘗試改為將 using 指示詞新增至檔案的開頭：

   ```csharp
   using CalculatorLibrary;
   ```

   這種變更應該可讓您從呼叫位置移除 CalculatorLibrary 命名空間，但現在有一個不明確的情況。 是 `Calculator` CalculatorLibrary 中的類別，還是計算機命名空間？  若要解決不明確的問題，請將命名空間重新命名 `CalculatorProgram` 。

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>參考 .NET 程式庫：寫入記錄檔

1. 假設您現在想要新增所有作業的記錄檔，並將它寫出至文字檔。 .NET `Trace` 類別提供這種功能。  (也適用于基本的列印偵錯工具。 ) Trace 類別是在 System.IO 中，而我們需要像這樣的類別 `StreamWriter` ，所以請從新增 using 指示詞開始：

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. 查看 Trace 類別的使用方式，您需要在與 filestream 相關聯的類別上保存參考。 這表示，計算機的運作方式會優於物件，所以讓我們加入一個函式。

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. 而且我們必須將靜態方法變更 `DoOperation` 為成員方法。  讓我們也將輸出新增至記錄檔的每個計算，讓 Dooperation-add-0.invoke 看起來像下列程式碼：

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. 現在回到 Program.cs，靜態呼叫會以紅色曲線標示。 若要修正此問題，請在 `calculator` while 迴圈之前新增下面這一行來建立變數：

   ```csharp
   Calculator calculator = new Calculator();
   ```

   以及修改的呼叫位置， `DoOperation` 如下所示：

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. 重新執行程式，然後在完成時，以滑鼠右鍵按一下專案節點，然後選擇 [ **在檔案總管中開啟資料夾**]，然後在檔案總管中向下流覽至輸出檔案夾。 它可能是 *bin/Debug/netcoreapp 3.1*，並且開啟了 [ *計算機] 記錄* 檔。

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>新增 NuGet 套件：寫入 JSON 檔案

1. 現在假設我們想要以 JSON 格式輸出作業，這是常用且可攜的格式，可用於儲存物件資料。 若要執行該功能，我們必須參考 Newtonsoft.Js上的 NuGet 套件。 NuGet 套件是發佈 .NET 類別庫的主要工具。 在 **方案總管** 中，以滑鼠右鍵按一下 CalculatorLibrary 專案的 [ **參考** ] 節點，然後選擇 [ **管理 NuGet 封裝**]。

   ![在快捷方式功能表上管理 NuGet 套件的螢幕擷取畫面](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet 封裝管理員隨即開啟。

   ![NuGet 套件管理員的螢幕擷取畫面](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. 搜尋套件上的 Newtonsoft.Js，然後選擇 [ **安裝**]。

   ![Newtonsoft NuGet 套件資訊的螢幕擷取畫面](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   封裝會下載並加入至您的專案，而新的專案會出現在 **方案總管** 的 [參考] 節點中。

1. 在 *CalculatorLibrary.cs* 的開頭加入 System.IO 和 Newtonsoft.Json 封裝的 using 指示詞。

   ```csharp
   using Newtonsoft.Json;
   ```

1. 現在以下列程式碼取代計算機的函式，然後建立 JsonWriter 成員物件：

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. 修改 `DoOperation` 方法以新增 JSON 寫入器程式碼：

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. 當使用者完成輸入作業資料之後，您將需要新增方法來完成 JSON 語法。

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. 在 *Program.cs* 中，新增在結尾處完成的呼叫。

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. 建立並執行應用程式，然後在完成輸入幾項作業之後，使用 ' n ' 命令將應用程式適當地關閉。  現在，開啟檔案 calculatorlog.js，您應該會看到如下的內容：

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Debug：設定和點擊中斷點

Visual Studio 偵錯工具是一項功能強大的工具，可讓您逐步執行程式碼，以找出發生程式設計錯誤的確切點。 然後，您會瞭解您需要在程式碼中進行哪些修正。 Visual Studio 可讓您進行暫時性變更，讓您可以繼續執行程式。

1. 在 [ *Program.cs*] 中，按一下下列程式碼左邊的邊界 (或開啟快捷方式功能表，然後選擇 [**中斷點**  >  **插入中斷點**]，或按下 **F9**) ：

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   出現的紅色圓圈表示中斷點。 您可以使用中斷點來暫停您的應用程式並檢查程式碼。 您可以在任何可執行檔程式程式碼上設定中斷點。

   ![設定中斷點的螢幕擷取畫面](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. 建置並執行應用程式。

1. 在正在執行的應用程式中，輸入一些計算值：

   - 針對第一個數位，輸入 **8** 並輸入。
   - 針對第二個數字，輸入0並輸入 **0** 。
   - 針對操作員，讓我們有一些有趣的東西，輸入 **d** ，然後輸入它。

   應用程式會暫停您建立中斷點的位置，這是由左邊的黃色指標和反白顯示的程式碼所表示。 反白顯示的程式碼尚未執行。

   ![點擊中斷點的螢幕擷取畫面](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   現在，在應用程式暫停的情況下，您可以檢查您的應用程式狀態。

## <a name="debug-view-variables"></a>Debug： view 變數

1. 在反白顯示的程式碼中，將滑鼠停留在變數上，例如 `cleanNum1` 和 `op` 。 您會看到這些變數目前的值 (`8` 和 `d` ，分別) 出現在資料提示中。

   ![查看資料提示的螢幕擷取畫面](media/vs-2019/calculator-2-debug-view-datatip.png)

   在進行偵錯工具時，檢查變數是否持有您預期的值，通常是修正問題的關鍵。

2. 在下方窗格中，查看 [ **區域變數** ] 視窗。  (如果已關閉，請選擇 [ **Debug**  >  **Windows**  >  **區域變數**] 來開啟它。 ) 

   在 [區域變數] 視窗中，您會看到目前在範圍中的每個變數，以及其值和類型。

   ![[區域變數] 視窗的螢幕擷取畫面](media/vs-2019/calculator-2-debug-locals-window.png)

3. 查看 **[自動** 變數] 視窗。

   [自動變數] 視窗類似于 [ **區域變數** ] 視窗，但它會顯示在您的應用程式暫停的目前程式程式碼前面和之後的變數。

   接下來，您將在偵錯工具中一次執行一個語句的程式碼，這稱為「 *逐步執行*」。

## <a name="debug-step-through-code"></a>Debug：逐步執行程式碼

1. 按 **F11** (或 **Debug**  >  **逐步** 執行) 。

   使用 [逐步執行] 命令，應用程式會執行目前的語句，並前進到下一個可執行檔語句， (通常是下一行程式碼) 。 左邊的黃色指標一律會指出目前的語句。

   ![逐步執行命令的螢幕擷取畫面](media/vs-2019/calculator-2-debug-step-into.png)

   您只是逐步執行 `DoOperation` 類別中的方法 `Calculator` 。

1. 若要取得程式流程的階層式查看，請查看 [ **呼叫堆疊** ] 視窗。  (如果已關閉，請選擇 [ **Debug**  >  **Windows**  >  **呼叫堆疊**]。 ) 

   ![呼叫堆疊的螢幕擷取畫面](media/vs-2019/calculator-2-debug-call-stack.png)

   這個視圖會顯示目前的 `Calculator.DoOperation` 方法（以黃色指標表示），而第二個數據列會顯示從 `Main` *Program.cs* 中的方法呼叫它的函式。 [呼叫堆疊] 視窗會顯示方法和函式的呼叫順序。 此外，它還可讓您從快捷方式功能表存取許多偵錯工具功能，例如 [ **移至原始程式碼**]。

1. 在   >  語句上暫停應用程式之前，請按下 F10 (或「偵錯工具不) 多次」 `switch` 。

   ```csharp
   switch (op)
   {
   ```

   [不進入函式] 命令類似于 [逐步執行] 命令，不同的是，如果目前的語句呼叫函式，偵錯工具會在呼叫的函式中執行程式碼，而不會暫停執行，直到函數傳回為止。 如果您對特定函式不感興趣，[不進入函式] 可以更快速地流覽程式碼。

1. 再按一次 **F10** ，讓應用程式在下列程式程式碼上暫停。

   ```csharp
   if (num2 != 0)
   {
   ```

   這段程式碼會檢查零除的情況。 如果應用程式繼續進行，則會擲回一般例外狀況 () 的錯誤，但假設您將此視為錯誤，並想要執行其他動作，例如在主控台中查看實際傳回的值。 其中一個選項是使用稱為「編輯後繼續」的偵錯工具功能來變更程式碼，然後繼續進行偵錯工具。 不過，我們將會為您示範不同的訣竅來暫時修改執行流程。

## <a name="debug-test-a-temporary-change"></a>Debug：測試暫時變更

1. 選取目前在語句上暫停的黃色指標， `if (num2 != 0)` 並將它拖曳至下列語句。

   ```csharp
   result = num1 / num2;
   ```

   如此一來，應用程式就會完全略過 `if` 語句，讓您可以看到當您零除時，會發生什麼事。

1. 按 **F10** 執行程式程式碼。

1. 將滑鼠停留在 `result` 變數上，您會看到它儲存的值 `Infinity` 。

   在 c # 中， `Infinity` 是以零除時的結果。

1. 按 **F5** (或， **Debug**  >  **繼續** 進行) 的調試。

   無限大符號會在主控台中顯示為數學運算的結果。

1. 使用 ' n ' 命令，正確地關閉應用程式。

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [繼續更多 C# 教學課程](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [繼續 Visual Studio IDE 總覽](/../visual-studio-ide.md)

## <a name="see-also"></a>另請參閱

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [了解如何在 Visual Studio 中偵錯 C# 程式碼](tutorial-debugger.md)
