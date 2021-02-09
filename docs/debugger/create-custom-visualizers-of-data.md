---
title: 建立自訂資料視覺化檢視 |Microsoft Docs
description: Visual Studio 偵錯工具視覺化程式是顯示資料的元件。 瞭解六個標準的視覺化檢視，以及您可以如何撰寫或下載其他視覺化檢視。
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f3d9a907d0857e918069fc4542d59d87242d609
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865835"
---
# <a name="create-custom-data-visualizers"></a>建立自訂資料視覺化檢視

 *視覺化* [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 程式是偵錯工具使用者介面的一部分，會以適合其資料類型的方式來顯示變數或物件。 例如，HTML 視覺化程式會解讀 HTML 字串，並顯示出現在瀏覽器視窗中的結果。 點陣圖視覺化檢視會解讀點陣圖結構，並顯示它所代表的圖形。 某些視覺化檢視可讓您修改和查看資料。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具包含六個標準視覺化檢視。 Text、HTML、XML 和 JSON 視覺化檢視適用于字串物件。 WPF 樹狀結構視覺化顯示 WPF 物件視覺化樹狀結構的屬性。 Dataset 視覺化檢視適用于 DataSet、DataView 和 DataTable 物件。

您可以從 Microsoft、協力廠商和社區下載更多的視覺化檢視。 您也可以撰寫自己的視覺化程式，並在偵錯工具中安裝它們 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 。

在偵錯工具中，視覺化檢視是以放大鏡圖示 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")表示。 您可以選取 [**資料提示**]、[偵錯工具監看式] 視窗或 [**快速****監看** 式] 對話方塊中的圖示，然後針對對應的物件選取適當的視覺化檢視。

## <a name="write-custom-visualizers"></a>撰寫自訂的視覺化檢視

 > [!NOTE]
 > 若要建立原生程式碼的自訂視覺化檢視，請參閱 [SQLite 原生偵錯工具視覺化程式](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) 範例。 UWP 和 Windows 8. x 應用程式不支援自訂的視覺化程式。

您可以為任何受控類別的物件撰寫自訂視覺化檢視，除了 <xref:System.Object> 和 <xref:System.Array> 以外。

偵錯工具視覺化檢視的架構分為兩部分：

- *偵錯工具端* 在 Visual Studio 偵錯工具內執行，並建立和顯示視覺化程式使用者介面。

- 「偵錯項目端」會在 Visual Studio 正在偵錯的處理序 (亦即「偵錯項目」) 中執行。 用來視覺化 (的資料物件，例如，) 存在於偵錯工具進程中的字串物件。 偵錯工具端會將物件傳送至偵錯工具端，這會顯示在您所建立的使用者介面中。

偵錯工具端會從執行介面的 *物件提供者* 接收資料物件 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 。 偵錯工具端會透過衍生自的 *物件來源* 傳送物件 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 。

物件提供者也可以將資料傳送回物件來源，讓您撰寫可編輯資料的視覺化檢視。 您可以覆寫物件提供者，以與運算式評估工具和物件來源交談。

偵錯工具端和偵錯工具端 <xref:System.IO.Stream> 會透過將資料物件序列化為的方法與彼此通訊 <xref:System.IO.Stream> ，並將 <xref:System.IO.Stream> 回還原序列化回資料物件。

只有當型別是開放式型別時，您才可以撰寫泛型型別的視覺化程式。 這項限制與使用 `DebuggerTypeProxy` 屬性時的限制相同。 如需詳細資訊，請參閱 [使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)。

自訂視覺化檢視會有安全性考量。 請參閱 [視覺化檢視安全性考慮](../debugger/visualizer-security-considerations.md)。

下列步驟提供視覺化建立視覺化的概要說明。 如需詳細指示，請參閱 <<c0> [ 逐步解說： 撰寫視覺化檢視C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)或是[逐步解說： 在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)。</c0>

### <a name="to-create-the-debugger-side"></a>若要建立偵錯工具端

若要在偵錯工具端建立視覺化程式使用者介面，您可以建立繼承自的類別， <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 並覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以顯示介面。 您可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 在視覺化程式中顯示 Windows form、對話方塊和控制項。

1. 請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法，取得偵錯工具端的視覺化物件。

1. 建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別。

1. 覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以顯示介面。 使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 方法在您的介面中顯示 Windows form、對話方塊和控制項。

4. 套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute> ，讓它顯示 () 的視覺化檢視 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 。

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>若要建立偵錯工具端的視覺化物件來源

在偵錯工具端程式碼中，編輯 <xref:System.Diagnostics.DebuggerVisualizerAttribute> ，並為其提供型別以視覺化 (偵錯工具端物件來源)  (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) 。 `Target`屬性會設定物件來源。 如果您省略物件來源，則視覺化檢視會使用預設的物件來源。

::: moniker range=">=vs-2019"
偵錯工具端程式碼包含可哥視化的物件來源。 資料物件可以覆寫的方法 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 。 如果您想要建立獨立的視覺化程式，則必須要有偵錯工具端 DLL。
::: moniker-end

在偵錯工具端程式碼中：

- 若要讓視覺化檢視編輯資料物件，物件來源必須繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ，並覆寫 `TransferData` 或 `CreateReplacementObject` 方法。

- 如果您需要在視覺化程式中支援多目標，您可以在偵錯工具端專案檔中使用下列目標 Framework 標記 (Tfm) 。

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   這些是唯一支援的 Tfm。

## <a name="see-also"></a>另請參閱

- [逐步解說：以 C# 撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [逐步解說：以 Visual Basic 撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [如何：對視覺化檢視進行測試和偵錯](../debugger/how-to-test-and-debug-a-visualizer.md)
- [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)
- [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)