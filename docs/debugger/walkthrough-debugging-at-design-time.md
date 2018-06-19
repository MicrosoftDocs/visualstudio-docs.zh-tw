---
title: 在設計階段-Visual Studio 偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c569ba018cfaa65cf2fec3edcf0676ef374db225
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476763"
---
# <a name="debug-at-design-time-in-visual-studio"></a>在 Visual Studio 中的設計階段偵錯

在某些情況下，您可能想要偵錯在設計的程式碼在執行應用程式，而不是時間。 您可以使用**即時運算**視窗。 如果您想要偵錯 XAML 互動的程式碼與其他程式碼，例如資料繫結程式碼，您可以使用**偵錯** > **附加至處理序**執行此作業。
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>偵錯在設計階段使用即時運算視窗  

您可以使用 Visual Studio**即時運算**視窗執行函式或副程式時不執行您的應用程式。 如果函式或副程式包含中斷點，Visual Studio 會在適當處中斷執行。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能稱為設計階段偵錯。  

下列範例是在 Visual Basic 中，但**即時運算**視窗也支援 C# 和 c + + 應用程式中。
  
1.  將下列程式碼貼到 Visual Basic 主控台應用程式：  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  讀取的行上設定中斷點`s="Add BreakPoint Here"`。  
  
3.  開啟**即時運算**視窗 (**偵錯** > **Windows** > **即時運算**) 輸入中的下列視窗： `?MyFunction<enter>`  
  
4.  請確認，叫用中斷點，和呼叫堆疊正確無誤。  
  
5.  在**偵錯**功能表上，按一下 **繼續**，並確認您是否仍在設計模式。  
  
6.  輸入中的下列**即時運算**視窗： `?MyFunction<enter>`  
  
7.  輸入中的下列**即時運算**視窗： `?MySub<enter>`  
  
8.  請確定您叫用中斷點，然後檢查靜態變數的值`i`中**區域變數**視窗。 它應該有值為 3。  
  
9. 驗證正確的呼叫堆疊。  
  
10. 在**偵錯**功能表上，按一下 **繼續**，並確認您是否仍在設計模式。  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>在 XAML 設計工具的設計階段偵錯

它可以是很有幫助偵錯從某些宣告式資料繫結案例中的 XAML 設計工具的程式碼後置。

1. 在專案中，加入新的 XAML 頁面，例如*temp.xaml*。 將新的 XAML 頁面保留空白。 

1. 編譯您的方案。

1. 開啟*temp.xaml*，載入設計工具 (*UwpSurface.exe*的 UWP 應用程式，或*XDesProc.exe*) 讓您可以在稍後步驟中，附加。 

1. 開啟新的 Visual Studio 執行個體。 在新的執行個體，開啟**附加至處理序**對話方塊 (**偵錯** > **附加至處理序**)，將**附加至**欄位的正確程式碼的型別，例如**Managed 程式碼 (CoreCLR)** 或正確的程式碼類型取決於您的.NET 版本。 從清單中選取正確的設計工具處理序，然後選擇 **附加**。

    Uwp 為目標的專案建置 16299 或以上版本，設計工具的程序是*UwpSurface.exe*。 WPF 或 UWP 的若是 16299 之前的版本，設計工具的程序是*XDesProc.exe*。

1. 附加至處理程序之後，切換至您的專案、 開啟程式碼後置您要偵錯，並設定中斷點。

1. 最後，開啟包含 XAML 程式碼，其中包含資料繫結的頁面。

    比方說，您無法針對下列 XAML，後者則在設計階段繫結 TextBlock 的類型轉換子的程式碼中設定中斷點。

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   當網頁載入時，會叫用中斷點。
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)
