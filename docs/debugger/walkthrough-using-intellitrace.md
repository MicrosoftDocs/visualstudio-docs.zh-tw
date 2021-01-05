---
title: 使用 IntelliTrace 來查看事件 |Microsoft Docs
description: 瞭解如何在 Visual Studio Enterprise 中使用 IntelliTrace 來收集特定事件、事件類別目錄和個別函式呼叫的相關資料。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fef839b5473881450581db77a885da158e67bbc
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815746"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>以 Visual Studio Enterprise (c #、Visual Basic) 中的 IntelliTrace 來查看事件

您可以使用 IntelliTrace 收集特定事件或事件分類的相關資訊，或是事件及個別函式呼叫的相關資訊。 下列程序說明如何執行此作業。

您可以在 Visual Studio Enterprise 版本 (而非 Professional 或 Community 版本) 中使用 IntelliTrace。

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> 設定 IntelliTrace

您可以嘗試只針對 IntelliTrace 事件進行偵錯。 IntelliTrace 事件是偵錯工具事件、例外狀況、.NET Framework 事件，以及其他系統事件。 您應在開始偵錯之前，先開啟或關閉特定事件，以控制 IntelliTrace 所記錄的事件。 如需詳細資訊，請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。

- 開啟檔案存取的 IntelliTrace 事件。 移至 [**工具 > 選項 > intellitrace > Intellitrace 事件**] 頁面，然後展開 [檔案 **] 分類。** 核取 [檔案]  事件分類。 這會核取所有的檔案事件 (存取、關閉、刪除)。

## <a name="create-your-app"></a>建立您的應用程式

1. 建立 C# 主控台應用程式。 在 Program.cs 檔案中，加入下列 `using` 陳述式：

    ```csharp
    using System.IO;
    ```

2. 在 Main 方法中建立 <xref:System.IO.FileStream> ，接著加以讀取、關閉，然後再刪除該檔案。 加入另一行，以設定中斷點：

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. 在 `Console.WriteLine("done");`上設定中斷點

## <a name="start-debugging-and-view-intellitrace-events"></a>開始調試和查看 IntelliTrace 事件

1. 照常開始偵錯  (按 **F5** 或按一下 [ **Debug] > 開始調試**。 ) 

    > [!TIP]
    > 當您在進行調試時，讓 [區域變數 **] 和 [** 自動 **變數**] 視窗保持開啟，以查看並記錄這些視窗中的值。

2. 執行會在中斷點停止。 如果您看不到 [ **診斷工具** ] 視窗，請按一下 [ **Debug > Windows > IntelliTrace 事件**]。

    在 [診斷工具]  視窗中，尋找 [事件]  索引標籤 (應有 3 個索引標籤：[事件] 、[記憶體使用量] 及 [CPU 使用量] )。 [事件]  索引標籤會依時間列出事件，其結尾會是偵錯工具中斷執行前的最後一個事件。 您應該會看到一個名為 **Access WordSearchInputs.txt** 的事件。

    下列螢幕擷取畫面來自 Visual Studio 2015 Update 1。

    ![Visual Studio 程式碼視窗的螢幕擷取畫面。 執行會在中斷點停止，且診斷工具視窗中的 [事件] 索引標籤會列出事件。](../debugger/media/intellitrace-update1.png)

3. 選取該事件，然後展開其詳細資料。

    下列螢幕擷取畫面來自 Visual Studio 2015 Update 1。

    ![[Visual Studio 診斷工具] 視窗中 [事件] 索引標籤的螢幕擷取畫面。 系統會選取並展開事件，以顯示其詳細資料。](../debugger/media/intellitraceupdate1-singleevent.png)

    您可以選擇路徑名稱連結來開啟該檔案。 如果無法使用完整路徑名稱，會顯示 [開啟檔案 ]  對話方塊。

    按一下 [ **啟用歷程記錄**]，將偵錯工具的內容設為所選事件的收集時間，並在 [ **呼叫堆疊**]、[ **區域變數** ] 及其他參與偵錯工具視窗中顯示歷程記錄資料。 如果原始程式碼可用，Visual Studio 會將指標移至對應來源視窗中的程式碼，因此您可以檢查它。

    下列螢幕擷取畫面來自 Visual Studio 2015 Update 1。

    ![Visual Studio 程式碼視窗的螢幕擷取畫面。 執行會在中斷點停止、選取事件，並反白顯示對應的程式程式碼。](../debugger/media/historicaldebugging-update1.png)

4. 如果沒有發現 Bug，請嘗試檢查導致 Bug 的其他事件。 您也可以讓 IntelliTrace 記錄呼叫資訊，以便您能逐步執行函式呼叫。

## <a name="next-steps"></a>後續步驟

您可以使用 IntelliTrace 的一些 advanced 功能與歷程記錄的偵錯工具：

- 若要查看快照集，請參閱 [使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)
- 若要瞭解如何檢查變數和流覽程式碼，請參閱 [使用歷程記錄來檢查應用程式](../debugger/historical-debugging-inspect-app.md)
