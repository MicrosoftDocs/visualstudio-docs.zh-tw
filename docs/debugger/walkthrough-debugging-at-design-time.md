---
title: 在設計階段偵錯 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf4a781bee0d0ccb1acd7d9c6b035acac603aea3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696697"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>在 Visual Studio 中的設計階段偵錯 (C#，c + +、 Visual Basic 中， F#)

執行程式碼偵錯在設計階段，而不是在應用程式時，您可以使用**Immediate**視窗。

您可以使用 XAML 設計工具中，例如資料繫結的程式碼，從應用程式背後的 XAML 程式碼偵錯**偵錯** > **附加至處理序**。

## <a name="use-the-immediate-window"></a>使用即時運算視窗

您可以使用 Visual Studio **Immediate**視窗來執行函式或副程式，而不需執行您的應用程式。 如果函式或副程式含有中斷點，Visual Studio 會在中斷點中斷。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能稱為*在設計階段偵錯*。

下列範例是在 Visual Basic 中。 您也可以使用**Immediate**視窗，在設計階段於C#， F#，和 c + + 應用程式。

1. 將下列程式碼貼到空白的 Visual Basic 主控台應用程式中：

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. 在該行設定中斷點**結束函式**。

1. 開啟**Immediate**視窗中的選取**偵錯** > **Windows** > **即時運算**。 型別`?MyFunction`視窗中，然後按**Enter**。

   中斷點是叫用，而**MyFunction**中**區域變數** 視窗會**1**。 在應用程式處於中斷模式時，您可以檢查呼叫堆疊和其他偵錯視窗。

1. 選取 **繼續**Visual Studio 工具列上。 結束應用程式，並**1**會傳回**即時運算**視窗。 請確定您仍處於設計模式。

1. 型別`?MyFunction`中**即時運算**視窗一次，再按下**Enter**。 中斷點是叫用，而**MyFunction**中**區域變數** 視窗會**2**。

1. 未選取**繼續**，型別`?MySub()`中**即時運算**視窗，然後再按**Enter**。 中斷點是叫用，而**MyFunction**中**區域變數** 視窗會**3**。 在應用程式處於中斷模式時，您可以檢查應用程式狀態。

1. 選取 **繼續**。 中斷點是叫用一次，而**MyFunction**中**區域變數** 視窗隨即**2**。 **Immediate**視窗會傳回**運算式已評估，而且沒有任何值**。

1. 選取 **繼續**一次。 結束應用程式，並**2**會傳回**即時運算**視窗。 請確定您是仍處於設計模式。

1. 若要清除的內容**Immediate**  視窗中，以滑鼠右鍵按一下視窗，然後選取**全部清除**。

## <a name="attach-to-an-app-from-the-xaml-designer"></a>從 XAML 設計工具附加至應用程式

在某些宣告式資料繫結案例中，它可以協助偵錯 XAML 設計工具中的程式碼後置。

1. 在 Visual Studio 專案中，加入新的 XAML 頁面，例如*temp.xaml*。 將新的 XAML 頁面保留空白。

1. 建置方案。

1. 開啟*temp.xaml*，載入 XAML 設計工具中， *XDesProc.exe*，或*UwpSurface.exe* UWP 應用程式中。

1. 開啟新的 Visual Studio 執行個體。 在新的執行個體中，選取**偵錯** > **附加至處理序**。

1. 在 **附加至處理序**對話方塊中，選取設計工具處理從**可用的處理序**清單。

   適用於 UWP 專案的目標 Windows 組建 16299 或更新版本，設計工具的處理序*UwpSurface.exe*。 對於之前 16299 WPF 或 UWP 版本，設計工具的程序相當*XDesProc.exe*。

1. 請確定**附加至**這類欄位設定為您的.NET 版本的正確程式碼型別**Managed 程式碼 (CoreCLR)**。

1. 選取 **附加**。

1. 附加至處理程序時，切換至其他 Visual Studio 執行個體，並設定您要偵錯您的應用程式背後的程式碼的中斷點。

   比方說，您可以在型別轉換子程式碼中設定中斷點，如下列 XAML，後者則繫結 TextBlock，在設計階段。

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   當頁面載入時，會叫用中斷點。

## <a name="see-also"></a>另請參閱
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [偵錯工具安全性](../debugger/debugger-security.md)