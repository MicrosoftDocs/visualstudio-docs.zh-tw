---
title: 偵錯受控程式碼 | Microsoft Docs
description: 使用 Visual Studio 偵錯工具來偵錯 C# 或 Visual Basic
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f790d30dc97d5549737c3c1cd003086477ce984f
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683016"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>快速入門：使用 Visual Studio 偵錯工具來進行 C# 或 Visual Basic 偵錯

Visual Studio 偵錯工具提供許多強大的功能，可協助您偵錯應用程式。 本主題提供了解一些基本功能的快速方法。

## <a name="create-a-new-project"></a>建立新專案

1. 開啟 Visual Studio 並建立新專案。

    ::: moniker range=">=vs-2019"
    如果 [開始] 視窗未開啟，請 **選擇 [** 檔案  >  **開始視窗]**。 在 [開始] 視窗中，選擇 [ **建立新專案**]。

    在 [建立新專案] 視窗的搜尋方塊中輸入或鍵入 ASP.NET。 接下來，從語言清單中選擇 **C#**，然後從平台清單中選擇 **Windows**。

    套用語言和平臺篩選器之後，請選擇適用于 .NET Core 的 **主控台應用程式** 範本，然後選擇 [ **下一步]**。

    選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

    如果您沒有看到適用于 .net Core 的 **主控台應用程式** 專案範本，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 **.Net Core 跨平臺開發** 工作負載，然後選擇 [ **修改**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新專案] 對話方塊的左窗格中，於 [Visual C#] 下選擇 [.NET Core]，然後在中間的窗格中選擇 [主控台應用程式 (.NET Core)]。 接著，輸入 **MyDbgApp** 之類的名稱，然後按一下 [確定]。

    如果您看不到 [主控台應用程式 (.NET Core)] 專案範本，請移至 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 **.Net Core 跨平臺開發** 工作負載，然後選擇 [ **修改**]。
    ::: moniker-end

    Visual Studio 會建立專案。

1. 在 *Program.cs* 或 *Module1.vb* 中，將下列程式碼

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    使用此程式碼取代：

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > 在 Visual Basic 中，確定啟始物件設定為 `Sub Main` ([屬性] > [應用程式] > [啟始物件])。

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」是一種標記，會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數值或記憶體行為，或查看程式碼分支是否正在執行。 它是偵錯中最基本的功能。

1. 若要設定中斷點，請按一下 `doWork` 函式呼叫左側的裝訂邊 (或選取該行程式碼並按 **F9** 鍵)。

    ![設定中斷點](../debugger/media/dbg-qs-set-breakpoint-csharp.png "設定中斷點")

2. 現在按下 **F5** 鍵 (或選擇 [偵錯] > [開始偵錯])。

    ![叫用中斷點](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "叫用中斷點")

    偵錯工具會在您設定中斷點的地方暫停。 暫停偵錯工具和應用程式執行所在的陳述式會以黃色箭號指示。 具有 `doWork` 函式呼叫的該行尚未執行。

    > [!TIP]
    > 如果在迴圈或遞迴中有中斷點，或是您有很多經常逐步執行的中斷點，請使用[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)，以確保程式碼只在符合特定條件時暫停。 條件中斷點可以節省時間，也可以讓您更輕鬆地偵錯難以重現的問題。

## <a name="navigate-code"></a>巡覽程式碼

您可以透過不同的命令來指示偵錯工具繼續。 我們會示出 Visual Studio 2017 開始可用的實用程式碼導覽命令。

在中斷點處暫停時，將滑鼠游標移至陳述式 `c1.AddLast(20)` 上方，直到出現綠色的 [執行至點選處] 按鈕 ![執行至點選處](../debugger/media/dbg-tour-run-to-click.png ">runtoclick")，然後按 [執行至點選處] 按鈕。

![執行以按一下](../debugger/media/dbg-qs-run-to-click-csharp.png "執行至點選處")

應用程式會繼續執行，並呼叫 `doWork`，然後在您按下按鈕所在的程式碼行暫停。

用來逐步執行程式碼的常用鍵盤命令包括 **F10** 和 **F11**。 如需詳細指示，請參閱[偵錯工具簡介](../debugger/debugger-feature-tour.md)。

## <a name="inspect-variables-in-a-data-tip"></a>檢查資料提示中的變數

1. 在目前的程式程式碼 (以黃色執行指標標示) ，將滑鼠停留在 `c1` 物件上，並以滑鼠顯示資料提示。

    ![查看資料提示](../debugger/media/dbg-qs-data-tip-csharp.png "查看資料提示")

    資料提示會顯示變數目前的值 `c1` ，並可讓您檢查其屬性。 偵錯時，如果您看到非預期的值，則前面的數行程式碼或呼叫的數行程式碼可能有 Bug。

2. 展開資料提示以查看物件目前的屬性值 `c1` 。

3. 如果您想要釘選資料提示，讓您可以在執行程式碼時繼續查看的值 `c1` ，請按一下 [小型釘選] 圖示。  (您可以將釘選的資料提示移至方便的位置。 ) 

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼並繼續偵錯

如果您在偵錯工作階段期間，於程式碼中找到要測試的變更，您也可以這麼做。

1. 按一下 `c2.First.Value` 的第二個執行個體，並將 `c2.First.Value` 變更為 `c2.Last.Value`。

2. 按幾下 **F10** 鍵 (或 [偵錯] > [不進入函式]) ，以繼續進行偵錯工具並執行編輯的程式碼。

    ![編輯後繼續](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "編輯後繼續")

    **F10** 鍵可讓偵錯工具一次前進一個陳述式，但不進入函式，藉此取代逐步執行 (您略過的程式碼仍會執行)。

如需使用編輯後繼續和功能限制的詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="next-steps"></a>下一步

在本教學課程中，您已了解如何啟動偵錯工具、逐步執行程式碼，以及檢查變數。 建議您進一步查看偵錯工具功能，以及詳細資訊的連結。

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
