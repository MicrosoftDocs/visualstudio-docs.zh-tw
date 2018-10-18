---
title: 在設計階段-Visual Studio 偵錯 |Microsoft Docs
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
ms.openlocfilehash: f1235e6360ccc5f6c0677f7ec9acb1dd85cad226
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180174"
---
# <a name="debug-at-design-time-in-visual-studio"></a>在 Visual Studio 中的設計階段偵錯

在某些情況下，您可能想要偵錯程式碼，在設計應用程式執行時，而不是時間。 您可以使用**Immediate**視窗。 如果您想要偵錯 XAML 互動的程式碼與其他程式碼，例如資料繫結的程式碼，您可以使用**偵錯** > **附加至處理序**若要這麼做。
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>在使用 [即時運算] 視窗的設計階段偵錯  

您可以使用 Visual Studio **Immediate**視窗，以在您的應用程式未在執行時執行函式或副程式。 如果函式或副程式含有中斷點，Visual Studio 會中斷執行的適當位置。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能稱為設計階段偵錯。  

下列範例是在 Visual Basic 中，但**Immediate**視窗也支援在 C# 和 c + + 應用程式。
  
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
  
3.  開啟**Immediate**  視窗 (**偵錯** > **Windows** > **即時運算**) 輸入中的下列視窗： `?MyFunction<enter>`  
  
4.  請確認，叫用中斷點，和呼叫堆疊正確無誤。  
  
5.  在 [**偵錯**] 功能表中，按一下**繼續**，並確認您是否仍處於設計模式。  
  
6.  輸入中的下列**Immediate**視窗： `?MyFunction<enter>`  
  
7.  輸入中的下列**Immediate**視窗： `?MySub<enter>`  
  
8.  確認您叫用中斷點，並檢查靜態變數的值`i`中**區域變數**視窗。 它應該有值為 3。  
  
9. 驗證正確的呼叫堆疊。  
  
10. 在 [**偵錯**] 功能表中，按一下**繼續**，並確認您是否仍處於設計模式。  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>在 XAML 設計工具的設計階段偵錯

它可以是偵錯程式碼後置 XAML 設計工具，在某些宣告式資料繫結案例中很有幫助。

1. 在您的專案中加入新的 XAML 頁面上，這類*temp.xaml*。 將新的 XAML 頁面保留空白。 

1. 編譯您的方案。

1. 開啟*temp.xaml*，其載入設計工具 (*UwpSurface.exe*在 UWP app 中，或*XDesProc.exe*) 讓您可以在稍後步驟中，連接。 

1. 開啟新的 Visual Studio 執行個體。 在新的執行個體，開啟**附加至處理序**  對話方塊 (**偵錯** > **附加至處理序**)，將**附加至**欄位的正確程式碼的型別，例如**Managed 程式碼 (CoreCLR)** 或正確的程式碼類型會根據您的.NET 版本。 從清單中選取正確的設計工具處理序，然後選擇**附加**。

    適用於 UWP 為目標的專案組建 16299 或更新版本，設計工具的處理序*UwpSurface.exe*。 對於 WPF 或 UWP 的 16299 之前的版本，設計工具的程序相當*XDesProc.exe*。

1. 附加至處理程序時，切換至您的專案，開啟程式碼後置您要偵錯，並設定中斷點。

1. 最後，開啟包含 XAML 程式碼，其中包含資料繫結的頁面。

    比方說，您可以在型別轉換子程式碼中設定中斷點，如下列 XAML，後者則繫結 TextBlock，在設計階段。

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   當頁面載入時，會叫用中斷點。
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/getting-started-with-the-debugger.md)
