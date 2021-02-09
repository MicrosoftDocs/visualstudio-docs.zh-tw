---
title: '教學課程：將 c # 和 c + + 程式碼 (混合模式進行偵錯工具) '
description: 了解如何使用混合模式偵錯，從 .NET Core 或 .NET Framework 應用程式偵錯原生 DLL
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 4b1d250ed5306ce101fd7482b740ad57514e4f0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899413"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>教學課程：在同一個偵錯工作階段中進行 C# 和 C++ 偵錯

Visual Studio 可讓您在偵錯工作階段中啟用多個偵錯工具類型，稱為混合模式偵錯。 在本教學課程中，您將了解如何在單一偵錯工作階段中，同時對受控程式碼與機器碼進行偵錯。

本教學課程示範如何從受控應用程式偵錯機器碼，但您也可[從原生應用程式偵錯受控程式碼](../debugger/how-to-debug-in-mixed-mode.md)。 此偵錯工具也支援其他類型的混合模式偵錯 (例如偵錯 [Python 和機器碼](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md))，並在 ASP.NET 等應用程式類型中使用指令碼偵錯工具。

在本教學課程中，您將：

> [!div class="checklist"]
> * 建立簡單的原生 DLL
> * 建立呼叫 DLL 的簡單 .NET Core 或 .NET Framework 應用程式
> * 設定混合模式偵錯
> * 啟動偵錯工具
> * 在受控應用程式中叫用中斷點
> * 逐步執行機器碼

## <a name="prerequisites"></a>必要條件

您必須安裝具有下列工作負載的 Visual Studio：
- **使用 C++ 開發桌面**
- **.NET 桌面開發** 或 **.NET Core 跨平台開發**，視您要建立的應用程式類型而定。

如果您沒有 Visual Studio，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) ] 頁面免費進行安裝。

如果您已安裝 Visual Studio，但沒有所需的工作負載，請在 Visual Studio [新增專案] 對話方塊的左窗格中，選取 [開啟 Visual Studio 安裝程式]。 在 Visual Studio 安裝程式中，選取您所需的工作負載，然後選取 [修改]。

## <a name="create-a-simple-native-dll"></a>建立簡單的原生 DLL

**若要建立 DLL 專案檔：**

1. 開啟 Visual Studio 並建立專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 輸入 **Ctrl + Q** 以開啟 [搜尋] 方塊，輸入 **空白專案**，選擇 [ **範本**]，然後選擇 [針對 c + + **空白專案** ]。 在出現的對話方塊中選擇 [建立]。 然後，鍵入像 **Mixed_Mode_Debugging** 的名稱，並按一下 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新專案] 對話方塊的左窗格中，於 [Visual C++] 下，選擇 [其他]，然後在中間的窗格中選擇 [空白專案]。 然後，鍵入像 **Mixed_Mode_Debugging** 的名稱，並按一下 [確定]。
    ::: moniker-end

    如果您未看到 [空白專案] 專案範本，請前往 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 Visual Studio 安裝程式即會啟動。 選擇 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

    Visual Studio 會建立專案。

1. 在 [方案總管] 中，選取 [來源檔案]，然後選取 [專案] > [新增項目]。 或者，以滑鼠右鍵按一下 [來源檔案]，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [C++ 檔 (.cpp)]。 在 [名稱] 欄位中，鍵入 **Mixed_Mode.cpp**，然後選取 [新增]。

    Visual Studio 隨即將新的 C++ 檔新增至 [方案總管]。

1. 將下列程式碼複製到 *Mixed_Mode.cpp* 中：

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. 在 [方案總管] 中，選取 [標頭檔]，然後選取 [專案] > [新增項目]。 或者，以滑鼠右鍵按一下 [標頭檔]，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [標頭檔 (.h)]。 在 [名稱] 欄位中，鍵入 **Mixed_Mode.h**，然後選取 [新增]。

   Visual Studio 隨即將新的標頭檔新增至 [方案總管]。

1. 將下列程式碼複製到 *Mixed_Mode.h* 中：

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. 選取  >  [**全部儲存**]，或按 **Ctrl** + **Shift** + **S** 以儲存檔案。

**若要設定並建置 DLL 專案：**

1. 在 Visual Studio 工具列中，選取 [偵錯] 組態，然後選取 [x86] 或 [x64] 平台。 如果您的呼叫應用程式將會是一律是在 64 位元模式執行的 .NET Core，請選取 [x64] 作為平台。

1. 在 [方案總管] 中，選取 **Mixed_Mode_Debugging** 專案節點，然後選取 **屬性** 圖示；或以滑鼠右鍵按一下專案節點，然後選取選取 [屬性]。

1. 在 [屬性] 窗格頂端，確定 [組態] 已設定 [作用中 (偵錯)]，且 [平台] 是您在工具列中設定的相同平台：[x64] (若為 x86 平台，則為 [Win32])。

   > [!IMPORTANT]
   > 如果您在 [x86] 與 [x64] 之間切換平台，則必須重新設定新平台的屬性。

1. 在左窗格的 [組態屬性] 下，選取 [連結器] > [進階]，然後在 [無進入點] 旁的下拉式清單中選取 [否]。 如果您必須將它變更為 [否]，請選取 [套用]。

1. 在 [組態屬性] 下，選取 [一般]，然後在 [組態類型] 旁的下拉式清單中選取 [動態程式庫 (.dll)]。 選取 [套用]  ，然後選取 [確定]  。

   ![切換至原生 DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. 在 [方案總管] 中選取專案，然後選取 [建置]**Build** > [建置方案]、按 **F7** 鍵，或以滑鼠右鍵按一下專案並選取 [建置]。

   專案應該會建置而無錯誤。

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>建立呼叫 DLL 的簡單受控應用程式

1. 開啟 Visual Studio 並建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 輸入 **Ctrl + Q** 以開啟 [搜尋] 方塊，輸入 **主控台**，選擇 [ **範本**]，然後選擇 [ **主控台應用程式 ( .net Core)** 或 **主控台應用程式 ( .NET Framework)** for c #。 在出現的對話方塊中選擇 [建立]。

    然後，鍵入像 **Mixed_Mode_Calling_App** 的名稱，並按一下 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新專案] 對話方塊的左窗格中，於 [Visual C#] 下選擇 [Windows Desktop]，然後在中間的窗格中選擇 [主控台應用程式 (.NET Framework)] 或 [主控台應用程式 (.NET Core)]。

    然後，鍵入像 **Mixed_Mode_Calling_App** 的名稱，並按一下 [確定]。
    ::: moniker-end

    如果您未看到 [主控台應用程式] 專案範本，請前往 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 **.net 桌面開發** 工作負載，然後選擇 [ **修改**]。

    > [!NOTE]
    > 您也可以將新的 managed 專案加入至現有的 c + + 方案。 我們要在新的方案中建立專案，讓混合模式的調試工作變得更困難。

   Visual Studio 會建立空白專案，並在 [方案總管] 中顯示。

1. 將 *Program.cs* 中的所有程式碼取代為下列程式碼：

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. 在新的程式碼中，將 `[DllImport]` 中檔案路徑取代為您剛建立的 *Mixed_Mode_Debugging.dll* 檔案路徑。 請參閱程式碼註解以取得提示。 請務必取代 *username* 預留位置。

1. 選取  >  [檔案 **儲存 Program.cs** ] 或按 **Ctrl** + **S** 以儲存檔案。

## <a name="configure-mixed-mode-debugging"></a>設定混合模式偵錯

1. 在 [方案總管] 中，選取 **Mixed_Mode_Calling_App** 專案節點，然後選取 **屬性** 圖示；或以滑鼠右鍵按一下專案節點，然後選取選取 [屬性]。

1. 在左窗格中選取 [偵錯]，選取 [啟用機器碼偵錯] 核取方塊，然後關閉屬性頁以儲存變更。

    ![啟用混合模式偵錯](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="set-a-breakpoint-and-start-debugging"></a>設定中斷點，並開始偵錯

1. 在 C# 專案中，開啟 *Program.cs*。 若要在下列程式碼行設定中斷點，請按一下最左邊，選取該行並按 **F9** 鍵，或以滑鼠右鍵按一下該行，然後選取 [中斷點] > [插入中斷點]。

    ```csharp
    int result = Multiply(7, 7);
    ```

    您設定中斷點的左邊界會出現紅色圓圈。

1. 按 **F5** 鍵、選取 Visual Studio 工具列中的綠色箭號，或選取 [偵錯] > [開始偵錯] 以開始偵錯。

   偵錯工具會在您設定的中斷點處暫停。 黃色箭號表示目前已暫停偵錯工具。

## <a name="step-in-and-out-of-native-code"></a>逐步執行和跳出機器碼

1. 當偵錯在受控應用程式中暫停時，按 **F11** 鍵，或選取 [偵錯] > [逐步執行]。

   *Mixed_Mode.h* 原生標頭檔隨即開啟，而且您會在偵錯工具的暫停位置看到黃色箭號。

   ![逐步執行機器碼](../debugger/media/mixed-mode-step-into-native-code.png)

1. 現在，您可以設定和叫用中斷點，並檢查機器碼或受控程式碼中的變數。

   - 將滑鼠游標移至原始程式碼中的變數上方以查看其值。

   - 在 [自動變數] 和 [區域變數] 視窗中，查看變數及其值。

   - 在偵錯工具中暫停時，您也可以使用 [監看式] 視窗和 [呼叫堆疊] 視窗。

1. 再按一次 **F11** 鍵，將偵錯工具前移一行。

1. 按 **Shift** + **F11** 或選取 [ **Debug**  >  **跳出**] 以繼續執行，然後在受管理的應用程式中再次暫停。

1. 按 **F5** 鍵或選取綠色箭號，以繼續偵錯應用程式。

恭喜！ 您已完成混合模式偵錯的教學課程。

## <a name="next-step"></a>後續步驟

在本教學課程中，您已了解如何啟用混合模式偵錯來從受控應用程式偵錯機器碼。 如需偵錯工具功能概觀，請參閱：

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
