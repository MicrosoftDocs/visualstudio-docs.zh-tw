---
title: 在設計階段進行 Debug |Microsoft Docs
description: 在設計階段使用 [即時運算] 視窗來進行程式碼的偵錯工具，而不執行應用程式。 您可以執行函數，並在叫用中斷點時檢查狀態。
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
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
ms.openlocfilehash: f127c630cec0e0b64ab5602e81f2b314a3896b16
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148843"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>在設計階段的 Visual Studio (c #、c + +/CLI、Visual Basic、F # ) 中進行調試

若要在設計階段（而不是在應用程式執行時）偵測程式碼，您可以 **使用 [即時** 運算] 視窗。

若要從 xaml 設計工具（例如宣告式資料系結案例）將應用程式的 XAML 程式碼進行偵錯工具，您可以使用 **debug**  >  **Attach 來處理**。

## <a name="use-the-immediate-window"></a>使用即時運算視窗

您可以 **使用 Visual Studio 即時** 運算視窗來執行函式或副程式，而不需要執行您的應用程式。 如果函式或副程式包含中斷點，Visual Studio 將會在中斷點中斷。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能 *在設計階段* 稱為「偵錯工具」。

下列範例位於 Visual Basic 中。 您也可以在 c #、F # 和 c + +/CLI 應用程式中，于設計階段 **使用 [即時** 運算] 視窗。

1. 將下列程式碼貼入空白的 Visual Basic 主控台應用程式中：

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

1. 在 line **End** 函式上設定中斷點。

1. 選取 [立即 **調試** 程式視窗 **]，開啟**[即時運算] 視窗  >    >  ****。 `?MyFunction`在視窗中輸入，然後按 **enter**。

   叫用中斷點，而 [**區域變數**] 視窗中的 **MyFunction** 值為 **1**。 當應用程式處於中斷模式時，您可以檢查呼叫堆疊和其他偵錯工具視窗。

1. 選取 Visual Studio 工具列上的 [ **繼續** ]。 應用程式會結束，並 **在 [即時** 運算] 視窗中傳回 **1** 。 請確定您仍處於設計模式。

1. `?MyFunction`再次在 [ 即時運算] 視窗中輸入，然後按 **enter**。 叫用中斷點，而 [**區域變數**] 視窗中的 [ **MyFunction** ] 的值為 **2**。

1. 如果未選取 [**繼續**]，請 `?MySub()` 在 [即時運算] 視窗中輸入，然後按 **enter** 鍵。  叫用中斷點，而 [**區域變數**] 視窗中的 **MyFunction** 值是 **3**。 當應用程式處於中斷模式時，您可以檢查應用程式狀態。

1. 選取 [繼續]。 會再次叫用中斷點，而 [**區域變數**] 視窗中的 **MyFunction** 值現在是 **2**。 [ **即時** 運算] 視窗傳回的 **運算式已經過評估，而且沒有任何值**。

1. 選取 [ **繼續** ]。 應用程式會結束，並 **在 [即時** 運算] 視窗中傳回 **2** 。 請確定您仍處於設計模式。

1. 若要清除 [即時運算 **] 視窗** 的內容，請在視窗中按一下滑鼠右鍵，然後選取 [ **全部清除**]。

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>藉由附加至 XAML 設計工具在設計階段進行自訂 XAML 控制項的偵錯工具

1. 在 Visual Studio 中開啟您的方案或專案。

1. 建立方案/專案。

1. 開啟包含您想要進行偵錯工具之自訂控制項的 XAML 頁面。

   針對以 Windows 組建16299或更新版本為目標的 UWP 專案，此步驟將會啟動 *UwpSurface.exe* 程式。 針對以 Windows 組建16299或更新版本為目標的 WPF 專案，此步驟將會啟動 *WpfSurface.exe* 進程。 針對 Windows 組建16299之前的 WPF 或 UWP 版本，此步驟將會啟動 *XDesProc.exe* 程式。 

1. 開啟 Visual Studio 的第二個執行個體。 請勿在第二個實例中開啟方案或專案。

1. 在 Visual Studio 的第二個實例中，開啟 [ **調試** 程式] 功能表，然後選擇 [ **附加至進程 ...**]。

1. 視您的專案類型而定 (請參閱先前的步驟) ，從可用的進程清單中選取 *UwpSurface.exe*、 *WpfSurface.exe* 或 *XDesProc.exe* 處理常式。

1. 在 [**附加至進程**] 對話方塊的 [**附加至**] 欄位中，為您想要進行偵錯工具的自訂控制項選擇正確的程式碼類型。

   如果您的自訂控制項是以 .NET 語言撰寫，請選擇適當的 .NET 程式碼類型，例如 **Managed (CoreCLR)**。 如果您的自訂控制項是以 c + + 撰寫，請選擇 [ **原生**]。

1. 按一下 [ **附加** ] 按鈕，以連接 Visual Studio 的第二個實例。

1. 在 Visual Studio 的第二個實例中，開啟與您要進行偵錯工具之自訂控制項相關聯的程式碼檔案。 請務必開啟檔案，而不是整個方案或專案。

1. 將必要的中斷點放在先前開啟的檔案中。

1. 在 Visual Studio 的第一個實例中，關閉包含您想要進行偵錯工具之自訂控制項的 XAML 頁面， (您在先前的步驟中開啟的相同頁面) 。

1. 在 Visual Studio 的第一個實例中，開啟您在上一個步驟中關閉的 XAML 頁面。 這會導致偵錯工具在您于第二個 Visual Studio 實例中設定的第一個中斷點停止。

1. 在 Visual Studio 的第二個實例中，進行程式碼的偵錯工具。

## <a name="see-also"></a>另請參閱
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [偵錯工具安全性](../debugger/debugger-security.md)