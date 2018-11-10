---
title: 教學課程： 偵錯 managed 和原生程式碼 （混合模式）
description: 了解如何從使用混合模式偵錯.NET Core 或.NET Framework 應用程式的原生 DLL 進行偵錯
ms.custom: ''
ms.date: 11/02/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295757"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>教學課程： 在相同的偵錯工作階段偵錯 managed 和原生程式碼

Visual Studio 可讓您啟用一個以上的偵錯工具類型稱為 「 混合模式偵錯的偵錯工作階段中。 在本教學課程中，您了解如何在單一的偵錯工作階段中偵錯 managed 和原生程式碼。 

本教學課程示範如何偵錯原生程式碼，從受管理的應用程式，但您也可以[偵錯 managed 程式碼與原生應用程式](../debugger/how-to-debug-in-mixed-mode.md)。 偵錯工具也支援其他類型的混合模式偵錯，例如偵錯[Python 和原生程式碼](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)，並在應用程式類型，例如 ASP.NET 中使用指令碼偵錯工具。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 建立簡單的原生 DLL
> * 建立簡單.NET Core 或.NET Framework 的應用程式呼叫 DLL
> * 設定混合模式偵錯
> * 開始偵錯工具
> * 叫用受管理的應用程式的中斷點
> * 逐步執行原生程式碼

## <a name="prerequisites"></a>必要條件

您必須安裝下列的工作負載的 Visual Studio:
- **使用 c + + 的桌面開發**
- 任一 **.NET 桌面開發**或是 **.NET Core 跨平台開發**，取決於您想要建立哪一種應用程式。

如果您沒有 Visual Studio，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 頁面，即可免費安裝它。

如果您已安裝 Visual Studio，但沒有您需要請選取工作負載**開啟的 Visual Studio 安裝程式**Visual Studio 的左窗格中**新的專案** 對話方塊。 在 Visual Studio 安裝程式中，選取 需要此項目，並選取您的工作負載**修改**。

## <a name="create-a-simple-native-dll"></a>建立簡單的原生 DLL

**若要建立 DLL 專案的檔案：**

1. 在 Visual Studio 中，選取**檔案** > **新增** > **專案**。

1. 在**新的專案**對話方塊的  **Visual c + +**，選取**其他**，然後選取**空專案**在中間窗格中。

1. 在 **名稱**欄位中，輸入**Mixed_Mode_Debugging**，然後選取**確定**。

   Visual Studio 會建立空的專案，並顯示在**方案總管 中**。

1. 在 [**方案總管] 中**，選取**原始程式檔**，然後選取**專案** > **加入新項目**。 或者，您也可以以滑鼠右鍵按一下**原始程式檔**，然後選取**新增** > **新項目**。 

1. 在 **新的項目**對話方塊中，選取**c + + 檔 (.cpp)**。 型別**Mixed_Mode.cpp**中**名稱**欄位，然後再選取**新增**。

    Visual Studio 會加入新的 c + + 檔案，以**方案總管 中**。

1. 下列程式碼複製到*Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. 在 [**方案總管] 中**，選取**標頭檔**，然後選取**專案** > **加入新項目**。 或者，您也可以以滑鼠右鍵按一下**標頭檔**，然後選取**新增** > **新項目**。 

1. 在 **新的項目**對話方塊中，選取**標頭檔 (.h)**。 型別**Mixed_Mode.h**中**名稱**欄位，然後再選取**新增**。

   Visual Studio 會加入新的標頭檔，以**方案總管 中**。

1. 下列程式碼複製到*Mixed_Mode.h*:

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

1. 選取 **檔案** > **全部儲存**或按**Ctrl**+**Shift**+**S**來儲存檔案。

**若要設定及建置 DLL 專案：**

1. 在 Visual Studio 工具列中，選取**偵錯**組態並**x86**或是**x64**平台。 如果您呼叫的應用程式將會是.NET Core，這一律是在 64 位元模式執行，請選取**x64**作為平台。

1. 在 [**方案總管] 中**，選取**Mixed_Mode_Debugging**專案節點，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案節點，然後選取**屬性**。

1. 在頂端**屬性**窗格中，確定**組態**設為**active （debug)** 和**平台**與您相同在工具列中設定： **x64**，或**Win32**適用於 x86 平台。 

   > [!IMPORTANT]
   > 如果您切換平台**x86**要**x64**或反之亦然，您必須重新設定新的平台的屬性。 

1. 底下**組態屬性**的左窗格中，選取**連結器** > **進階**，以及旁的下拉式清單中**沒有進入點**，選取**No**。 如果您必須將它變更為**No**，選取**套用**。

1. 底下**組態屬性**，選取**一般**，和旁的下拉式清單中**組態類型**，選取**動態程式庫 (.dll)**. 選取 **套用**，然後選取**確定**。

   ![切換至原生 DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. 中，選取專案**方案總管**，然後選取**建置** > **建置方案**，按下**F7**，或以滑鼠右鍵按一下專案，然後選取**建置**。

   未出現任何錯誤，應該可以建置專案。

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>建立簡單的受管理應用程式呼叫 DLL

1. 在 Visual Studio 中，選擇**檔案** > **新增** > **專案**。

   > [!NOTE]
   > 雖然您也無法將新的受管理的專案加入至您現有的 c + + 方案中，建立新的解決方案支援更多偵錯案例。

1. 在 **新的專案**對話方塊中，選取**Visual C#** ，並在中間窗格中：

   - .NET Framework 應用程式中，選取**主控台應用程式 (.NET Framework)**。
   
   - .NET Core 應用程式中，選取**主控台應用程式 (.NET Core)**。

1. 在 **名稱**欄位中，輸入**Mixed_Mode_Calling_App**，然後選取**確定**。

   Visual Studio 會建立空的專案，並顯示在**方案總管 中**。

1. 中的所有程式碼取代*Program.cs*為下列程式碼：

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

1. 在新的程式碼，來取代中的檔案路徑`[DllImport]`以您的檔案路徑*Mixed_Mode_Debugging.dll*您剛剛建立。 提示的程式碼註解，請參閱。 請務必取代*username*預留位置。

1. 選取 **檔案** > **儲存 Program.cs**或按**Ctrl**+**S**來儲存檔案。

## <a name="configure-mixed-mode-debugging"></a>設定混合模式偵錯 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>若要設定混合模式偵錯的.NET Framework 應用程式 

1. 在 [**方案總管] 中**，選取**Mixed_Mode_Calling_App**專案節點，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案節點，然後選取**屬性**。

1. 選取 **偵錯**的左窗格中，選取**啟用機器碼偵錯**核取方塊，，然後關閉 內容 頁面，以儲存變更。

    ![啟用混合的模式偵錯](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>若要設定混合模式偵錯.NET Core 應用程式 

在大部分的 Visual Studio 2017 版本中，您必須使用*launchSettings.json*檔案而不是專案屬性，以啟用混合模式偵錯的.NET Core 應用程式中的原生程式碼。 若要追蹤這項功能的 UI 更新，請參閱這[GitHub 問題](https://github.com/dotnet/project-system/issues/1125)。

1. 在 [**方案總管] 中**，展開**屬性**，並開啟*launchSettings.json*檔案。 

   >[!NOTE]
   >根據預設， *launchSettings.json*處於*C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*。 如果*launchSettings.json*不存在，請選取**Mixed_Mode_Calling_App**專案**方案總管 中**，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案，然後選取**屬性**。 進行中的暫存變更**偵錯**索引標籤，然後建置專案。 這會建立*launchSettings.json*檔案。 還原您在中所做的變更**偵錯** 索引標籤。

1. 在  *lauchsettings.json*檔案中，新增下面這一行：

    ```csharp
    "nativeDebugging": true
    ```

    完整的檔案看起來如下列範例所示：

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>設定中斷點並開始偵錯

1. 在C#專案中，開啟*Program.cs*。 下列程式碼行上設定中斷點，最左邊界中按一下，選取線條，然後按**F9**，或以滑鼠右鍵按一下該行，然後選取**中斷點** >  **插入中斷點**。

    ```csharp
    int result = Multiply(7, 7);
    ```

    紅色圓圈會出現在左邊界，您在其中設定中斷點。

1. 按下**F5**，在 Visual Studio 工具列中，選取綠色箭號，或選取**偵錯** > **開始偵錯**開始偵錯。

   偵錯工具會在您設定的中斷點上暫停。 黃色箭號表示目前已偵錯工具暫停。

## <a name="step-in-and-out-of-native-code"></a>縮小和相應放大的原生程式碼步驟

1. 當偵錯暫停中受管理的應用程式時，按下**F11**，或選取**偵錯** > **逐步執行**。

   *Mixed_Mode.h*原生的標頭檔隨即開啟，而且您看到偵錯工具暫停時，黃色箭號。

   ![逐步執行原生程式碼](../debugger/media/mixed-mode-step-into-native-code.png)

1. 現在，您可以設定和叫用中斷點並檢查在原生或 managed 程式碼中的變數。

   - 將滑鼠停留在 原始碼，以查看其值的變數。

   - 看看變數和值**自動變數**並**區域變數**windows。

   - 當偵錯工具暫停時，您也可以使用**監看式**windows 並**呼叫堆疊**視窗。

1. 按下**F11**一次，讓偵錯工具一列。

1. 按下**Shift**+**F11** ，或選取**偵錯** > **跳離函式**若要繼續執行，然後再次在暫停受管理的應用程式。

1. 按下**F5**或選取綠色箭頭以繼續偵錯應用程式。

恭喜您！ 您已完成本教學課程的混合模式偵錯。

## <a name="next-step"></a>後續步驟

在本教學課程中，您已了解如何藉由啟用混合模式偵錯，從受管理的應用程式的原生程式碼進行偵錯。 如需其他偵錯工具功能的概觀，請參閱：

> [!div class="nextstepaction"]
> [偵錯工具簡介](../debugger/debugger-feature-tour.md)
