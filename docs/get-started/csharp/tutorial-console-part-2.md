---
title: '教學課程：擴充簡單的 c # 主控台應用程式'
description: '瞭解如何 Visual Studio 逐步開發 c # 主控台應用程式。'
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aae83c43a106fd68b03a83124ad2ddcea4652c8d
ms.sourcegitcommit: c620d59578db1b89f80e64ae04b4898bc4ab292d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377141"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>教學課程：擴充簡單的 c # 主控台應用程式

在本教學課程中，您將瞭解如何使用 Visual Studio 來擴充您在第一個部分中建立的主控台應用程式。 您將瞭解 Visual Studio 中的一些功能，可協助您以開發人員的身分提高生產力，例如使用 advanced editor 功能和偵錯工具。

如果您剛完成此系列的[第一個部分](tutorial-console.md)，則您已經有計算機主控台應用程式。  若要略過第1部分，您可以從 GitHub 存放庫開啟專案開始。 C # 計算機應用程式位於 vs 教學課程[-範例](https://github.com/MicrosoftDocs/vs-tutorial-samples)存放庫中，因此您可以直接依照教學課程[：從存放庫開啟專案](../tutorial-open-project-from-repo.md)以開始使用中的步驟進行。

## <a name="add-a-new-project"></a>新增專案

真實世界的程式碼牽涉到許多專案一起在解決方案中運作。 現在，讓我們將另一個專案新增至計算機應用程式。 這會是提供一些計算機函數的類別庫。

1. 在 Visual Studio 中，您可以使用最上層**功能表命令檔**[  >  **加入**  >  **新專案**] 來加入新的專案，但您也可以在現有的專案名稱（稱為「專案節點」）上按一下滑鼠右鍵，然後開啟專案的快捷方式功能表（或操作功能表）。 這個快捷方式功能表包含許多方法，可以將功能加入至您的專案。 因此，以滑鼠右鍵按一下**方案總管**中的專案節點，然後選擇 [**加入**  >  **新專案**]。

1. 選擇 c # 專案範本**類別庫（.NET Standard）**。

   ![類別庫專案範本選取的螢幕擷取畫面](media/vs-2019/calculator2-add-project-dark.png)

1. 輸入專案名稱**CalculatorLibrary**，然後選擇 [**建立**]。 Visual Studio 會建立新的專案，並將其新增至方案。

   ![已加入 CalculatorLibrary 類別庫專案之方案總管的螢幕擷取畫面](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. 請重新命名檔案**CalculatorLibrary.cs**，而不是*Class1.cs*。 您可以按一下**方案總管**中的名稱將其重新命名，或以滑鼠右鍵按一下並選擇 [**重新命名**]，或按**F2**鍵。

   系統可能會詢問您是否要重新命名檔案中的任何參考 `Class1` 。 您的回答方式並不重要，因為您將會在未來的步驟中取代程式碼。

1. 我們現在必須加入專案參考，讓第一個專案可以使用新類別庫所公開的 Api。  以滑鼠右鍵按一下第一個專案中的 [**參考**] 節點，然後選擇 [**加入專案參考**]。

   ![[加入專案參考] 功能表項目的螢幕擷取畫面](media/vs-2019/calculator2-add-project-reference-dark.png)

   [參考管理員]**** 對話方塊隨即顯示。 這個對話方塊可讓您加入其他專案的參考，以及您的專案所需的元件和 COM Dll。

   ![[參考管理員] 對話方塊的螢幕擷取畫面](media/vs-2019/calculator2-ref-manager-dark.png)

1. 在 [**參考管理員**] 對話方塊中，選取 [ **CalculatorLibrary** ] 專案的核取方塊，然後選擇 **[確定]**。  專案參考會出現在**方案總管**的 [**專案**] 節點底下。

   ![具有專案參考之方案總管的螢幕擷取畫面](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. 在 [ *Program.cs*] 中，選取 `Calculator` 類別及其所有程式碼，然後按**CTRL + X**將其從 Program.cs 剪下。 然後在**CalculatorLibrary**的*CalculatorLibrary.cs*中，將程式碼貼到 `CalculatorLibrary` 命名空間中。 然後，將計算機類別設 `public` 為在程式庫外部公開。 *CalculatorLibrary.cs*中的程式碼現在應該類似下列程式碼：

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

1. 第一個專案有參考，但您會看到 Dooperation-add-0.invoke 呼叫無法解析的錯誤。 這是因為 CalculatorLibrary 是在不同的命名空間中，因此，請 `CalculatorLibrary` 為完整的參考加入命名空間。

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   請嘗試將 using 指示詞新增至檔案的開頭，改為：

   ```csharp
   using CalculatorLibrary;
   ```

   這種變更應該可讓您從呼叫位置移除 CalculatorLibrary 命名空間，但現在有一個不明確的。 是 `Calculator` CalculatorLibrary 中的類別，還是計算機命名空間？  若要解決不明確的問題，請將命名空間重新命名 `CalculatorProgram` 。

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>參考 .NET 程式庫：寫入記錄檔

1. 假設您現在想要新增所有作業的記錄檔，並將其寫出至文字檔。 .NET `Trace` 類別提供這種功能。 （它也適用于基本的列印偵錯工具技術）。 Trace 類別位於 Diagnostics 中，因此請從新增 using 指示詞開始：

   ```csharp
   using System.Diagnostics;
   ```

1. 查看 Trace 類別的使用方式，您需要保留與 filestream 相關聯之類別的參考。 這表示，計算機會以物件的效果更好，因此，讓我們來加入一個函式。

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

1. 而且我們需要將靜態方法變更 `DoOperation` 為成員方法。  讓我們也將輸出新增到記錄檔的每個計算中，讓 Dooperation-add-0.invoke 看起來像下列程式碼：

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

1. 現在回到 Program.cs，靜態呼叫會以紅色曲線標示。 若要修正此問題，請在 `calculator` while 迴圈前面加入下面這一行來建立變數：

   ```csharp
   Calculator calculator = new Calculator();
   ```

   和會修改的呼叫位置，如下所示 `DoOperation` ：

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. 再次執行程式，並在完成時，以滑鼠右鍵按一下專案節點，然後選擇 [**在檔案瀏覽器中開啟資料夾**]，然後在 [檔案瀏覽器] 中流覽至輸出檔案夾。 它可能是*bin/Debug/netcoreapp 3.1*，而是開啟*計算機 .log*檔案。

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>新增 NuGet 套件：寫入 JSON 檔案

1. 現在假設我們想要以 JSON 格式輸出作業，這是一種常用且可移植的格式，用於儲存物件資料。 若要執行這種功能，我們必須參考 Newtonsoft.Js上的 NuGet 套件。 NuGet 套件是用來散發 .NET 類別庫的主要車輛。 在**方案總管**中，以滑鼠右鍵按一下 CalculatorLibrary 專案的 [**參考**] 節點，然後選擇 [**管理 NuGet 封裝**]。

   ![快捷方式功能表上的 [管理 NuGet 套件] 的螢幕擷取畫面](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   [NuGet 套件管理員] 隨即開啟。

   ![NuGet 套件管理員的螢幕擷取畫面](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. 在 [套件] 上搜尋 Newtonsoft.Js，然後選擇 [**安裝**]。

   ![Newtonsoft NuGet 套件資訊的螢幕擷取畫面](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   系統會下載封裝，並將其新增至您的專案，並在**方案總管**的 [參考] 節點中出現新的專案。

1. 在*CalculatorLibrary.cs*開頭的封裝上，為 Newtonsoft.Js新增 using 指示詞。

   ```csharp
   using Newtonsoft.Json;
   ```

1. 現在，以下列程式碼取代計算機的函式，並建立 JsonWriter 成員物件：

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

1. 當使用者完成輸入作業資料之後，您必須新增方法來完成 JSON 語法。

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. 在*Program.cs*中，新增在結尾處完成的呼叫。

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. 建立並執行應用程式，在您完成輸入幾項作業之後，請使用 ' n ' 命令適當地關閉應用程式。  現在，開啟檔案上的 consolelog.js，您應該會看到如下所示的內容：

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

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 若要更深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [繼續更多 C# 教學課程](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [繼續進行 Visual Studio IDE 總覽](/../visual-studio-ide.md)

## <a name="see-also"></a>另請參閱

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [了解如何在 Visual Studio 中偵錯 C# 程式碼](tutorial-debugger.md)
