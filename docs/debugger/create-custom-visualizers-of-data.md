---
title: "建立自訂的視覺化檢視的資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.visualizer.troubleshoot
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
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 23985c56ba61e5a788232523611a48cfde902335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-visualizers-of-data"></a>建立自訂的視覺化檢視的資料
 視覺化檢視是元件的[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]偵錯工具使用者介面。 A*視覺化檢視*建立對話方塊或另一個介面是適用於其資料類型的方式顯示變數或物件。 例如，HTML 視覺化檢視會解譯 HTML 字串，並在瀏覽視窗中顯示出現的結果，而點陣圖視覺化檢視會解譯點陣圖結構，並顯示其所代表的圖形。 除了檢視資料外，有些視覺化檢視也能讓您修改資料。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具包含六個標準視覺化檢視。 這些是文字、 HTML、 XML 及 JSON 視覺化檢視，全部都是用於字串物件。WPF 樹狀架構視覺化檢視，來顯示 WPF 物件視覺化樹狀，屬性和資料集視覺化檢閱則適用於資料集、 DataView 和 DataTable 物件。 額外的視覺化檢視未來可能可以從 Microsoft Corporation 下載，且可從協力廠商和社群取得。 此外，您可以自行撰寫視覺化檢視，並將它們安裝至 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具中。

 > [!NOTE]
 > 若要建立原生程式碼的自訂視覺化檢視，請參閱[SQLite 原生偵錯工具視覺化檢視](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)範例。 在 UWP 和 Windows 8.x 應用程式，不支援自訂視覺化檢視。

 在偵錯工具中，視覺化檢視會以放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 當您看到的放大鏡圖示**DataTip**，在偵錯工具視窗中，例如**監看式**視窗中，或在**快速監看式**對話方塊中，您可以按一下放大鏡，選取適用於資料類型的對應物件的視覺化檢視。

## <a name="overview-of-custom-visualizers"></a>自訂視覺化檢視的概觀

您可以為任何 Managed 類別的物件撰寫自訂視覺化檢視，除了 <xref:System.Object> 或 <xref:System.Array> 以外。  
  
 偵錯工具視覺化檢視的架構分為兩部分：  
  
-   *偵錯工具端*Visual Studio 偵錯工具內執行。 偵錯工具端的程式碼會建立並顯示視覺化檢視的使用者介面。  
  
-   *偵錯項目端*Visual Studio 偵錯的程序中執行 (*偵錯項目*)。  
  
 您要進行視覺化的資料物件 (例如，String 物件) 會存在於偵錯項目處理序中。 因此，偵錯項目端必須將該資料物件傳送至偵錯工具端，然後偵錯工具端才能使用您建立的使用者介面顯示這個資料物件。  
  
 偵錯工具端會收到這個資料物件，若要從以視覺化方式檢視*物件提供者*實作<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>介面。 偵錯項目端會將資料物件，透過傳送*物件來源*，其衍生自<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。 物件提供者也可以將資料送回物件來源，以便您撰寫可編輯和顯示資料的視覺化檢視。 物件提供者可被覆寫，以便與運算式評估工具進行溝通，也就是與物件來源溝通。  
  
 偵錯項目端和偵錯工具端是透過 <xref:System.IO.Stream> 相互溝通。 提供的方法是用來將資料物件序列化至 <xref:System.IO.Stream>，並將 <xref:System.IO.Stream> 還原序列化至資料物件中。  
  
 偵錯項目端的程式碼是使用 DebuggerVisualizer 屬性 (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) 進行指定。  
  
 若要在偵錯工具端建立視覺化檢視使用者介面，您必須建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別，並覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法顯示此介面。  
  
 您可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>，從您的視覺化檢視顯示 Windows Form、對話方塊和控制項。  
  
 對泛型類型的支援是有限的。 只有在泛型類型是開啟類型時，才能夠為泛型類型目標撰寫視覺化檢視。 這項限制與使用 `DebuggerTypeProxy` 屬性時的限制相同。 如需詳細資訊，請參閱[使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
 自訂視覺化檢視會有安全性考量。 請參閱[視覺化檢視安全性考量](../debugger/visualizer-security-considerations.md)。  
  
 下列程序提供在建立視覺化檢視時所需的概觀。 如需更詳細的說明，請參閱[逐步解說： 在 C# 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。  
  
### <a name="to-create-the-debugger-side"></a>若要建立偵錯工具端  
  
1.  請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法，取得偵錯工具端的視覺化物件。  
  
2.  建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別。  
  
3.  覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以顯示介面。 使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 方法以將 Windows Form、對話方塊和控制項顯示為介面的一部分。  
  
4.  套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，並賦予它一個視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>若要建立偵錯項目端  
  
1.  套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，並賦予它一個視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) 和物件來源 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)。 如果您忽略了物件來源，將使用預設的物件來源。  
  
2.  如果您希望視覺化檢視能夠編輯和顯示資料物件，您必須從 `TransferData` 覆寫 `CreateReplacementObject` 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 方法。   
  
## <a name="in-this-section"></a>本節內容
  
 [逐步解說：在 C# 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [逐步解說：在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：測試和偵錯視覺化檢視](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>相關章節  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)