---
title: 建立自訂的資料視覺化檢視 |Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607818"
---
# <a name="create-custom-data-visualizers"></a>建立自訂的資料視覺化檢視 
 A*視覺化檢視*屬於[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]適用於其資料類型的方式顯示變數或物件的偵錯工具使用者介面。 例如，HTML 視覺化檢視會解譯 HTML 字串，並顯示結果，就會出現在瀏覽器視窗中。 而點陣圖視覺化檢視會解譯點陣圖結構，並顯示它所代表的圖形。 有些視覺化檢視可讓您修改，以及檢視資料。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具包含六個標準視覺化檢視。 文字、 HTML、 XML 及 JSON 視覺化檢視作用於字串物件。 WPF 樹狀架構視覺化檢視會顯示 WPF 物件視覺化樹狀結構的屬性。 資料集視覺化檢視適用於資料集、 DataView 和 DataTable 物件。 

多個視覺化檢視可能可以從 Microsoft、 協力廠商和社群下載。 您也可以自行撰寫視覺化檢視，並安裝在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]偵錯工具。

在 偵錯工具中，視覺化檢視以放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 您可以選取中的圖示**DataTip**，偵錯工具**監看式**視窗中，或**快速監看式**對話方塊中，然後選取適當的視覺化檢視對應的物件。

## <a name="write-custom-visualizers"></a>撰寫自訂視覺化檢視

 > [!NOTE]
 > 若要建立原生程式碼的自訂視覺化檢視，請參閱[SQLite 原生偵錯工具視覺化檢視](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)範例。 UWP 和 Windows 8.x 應用程式不支援自訂視覺化檢視。

您可以撰寫自訂視覺化檢視物件的任何受管理的類別，除了<xref:System.Object>和<xref:System.Array>。  
  
偵錯工具視覺化檢視的架構分為兩部分：  
  
- *偵錯工具端*執行 Visual Studio 偵錯工具中，會建立並顯示視覺化檢視使用者介面。  
  
- *偵錯項目端*Visual Studio 偵錯處理序內執行 (*偵錯項目*)。 偵錯項目處理序中，有要以視覺化方式檢視 （例如，字串物件） 的資料物件。 在偵錯項目端會將物件傳送至偵錯工具端，以顯示您所建立的使用者介面中。  

偵錯工具端接收資料物件從*物件提供者*可實<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>介面。 在偵錯項目端會傳送物件，可透過*物件來源*，其係衍生自<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。 

物件提供者也可以將資料送回物件來源，可讓您撰寫視覺化檢視，可以編輯資料。 您覆寫與運算式評估工具和物件來源的物件提供者。  
  
偵錯項目和偵錯工具端之間的通訊方式透過<xref:System.IO.Stream>方法將序列化資料物件插入<xref:System.IO.Stream>和還原序列化<xref:System.IO.Stream>回資料物件。  

只有類型為開啟類型，您可以撰寫視覺化檢視針對泛型型別。 這項限制與使用 `DebuggerTypeProxy` 屬性時的限制相同。 如需詳細資訊，請參閱 <<c0> [ 使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
自訂視覺化檢視會有安全性考量。 請參閱[視覺化檢視安全性考量](../debugger/visualizer-security-considerations.md)。  
  
下列步驟提供視覺化檢視建立的高階概觀。 如需詳細指示，請參閱 <<c0> [ 逐步解說： 撰寫視覺化檢視C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)或是[逐步解說： 在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)。</c0>  
  
### <a name="to-create-the-debugger-side"></a>若要建立偵錯工具端  
  
若要建立偵錯工具端視覺化檢視使用者介面，您會建立繼承自類別<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>，並覆寫<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>方法，以顯示介面。 您可以使用<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>視覺化檢視中顯示 Windows form、 對話方塊和控制項。  
  
1.  請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法，取得偵錯工具端的視覺化物件。  
  
1.  建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別。  
  
1.  覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以顯示介面。 使用<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>介面中顯示 Windows form、 對話方塊和控制項的方法。  
  
4.  適用於<xref:System.Diagnostics.DebuggerVisualizerAttribute>，讓它顯示視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>若要建立偵錯項目端  
  
使用指定偵錯項目端程式碼<xref:System.Diagnostics.DebuggerVisualizerAttribute>。  
  
1.  套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，並賦予它一個視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) 和物件來源 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)。 如果您省略物件來源，視覺化檢視會使用預設的物件來源。  
  
1.  若要讓編輯，以及顯示的資料物件的視覺化檢視，請覆寫`TransferData`或是`CreateReplacementObject`方法從<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。   
  
## <a name="see-also"></a>另請參閱
  
 [逐步解說：使用 C# 撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [逐步解說：使用 Visual Basic 撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：對視覺化檢視進行測試和偵錯](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)  
  
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)