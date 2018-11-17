---
title: 視覺化檢視架構 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7a3255b8e8b91f074308a0238719f26af6cf665
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736149"
---
# <a name="visualizer-architecture"></a>視覺化檢視架構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

偵錯工具視覺化檢視的架構分為兩部分：  
  
- *偵錯工具端*Visual Studio 偵錯工具內執行。 偵錯工具端的程式碼會建立並顯示視覺化檢視的使用者介面。  
  
- *偵錯項目端*Visual Studio 偵錯處理序內執行 (*偵錯項目*)。  
  
  視覺化檢視是可讓偵錯工具顯示的偵錯工具元件 (*視覺化*) 中有意義、 容易了解表單的資料物件的內容。 有些視覺化檢視也支援編輯資料物件。 您可以撰寫自訂的視覺化檢視，來將偵錯工具擴充成可以處理自己的自訂資料型別。  
  
  要視覺化的資料物件位於您正在偵錯的程序 (*偵錯項目*程序)。 即將顯示資料的使用者介面則在 Visual Studio 偵錯工具處理序內建立：  
  
|偵錯工具處理序|偵錯項目處理序|  
|----------------------|----------------------|  
|偵錯工具使用者介面 (資料提示方塊、監看式視窗、快速監看式)|要視覺化的資料物件|  
  
 若要在偵錯工具介面中將資料物件視覺化，您必須編寫兩個處理序之間的通訊程式碼。 因此，視覺化檢視架構是由兩個部分所組成：*偵錯工具端*程式碼並*偵錯項目端*程式碼。  
  
 偵錯工具端程式碼會建立自己的使用者介面，供您從偵錯工具介面 (例如，資料提示方塊、監看式視窗或快速監看式) 中叫用。 建立視覺化檢視介面是使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 類別和 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 介面。 DialogDebuggerVisualizer 和 IDialogVisualizerService 跟所有視覺化檢視 API 一樣位於 <xref:Microsoft.VisualStudio.DebuggerVisualizers> 命名空間中。  
  
|偵錯工具端|偵錯項目端|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer 類別<br /><br /> IDialogVisualizerService 介面|資料物件|  
  
 使用者介面會從偵錯工具端上的物件提供者處取得要視覺化的資料：  
  
|偵錯工具端|偵錯項目端|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer 類別<br /><br /> IDialogVisualizerService 介面|資料物件|  
|物件提供者 (實作 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 偵錯項目端有對應的物件，稱為物件來源：  
  
|偵錯工具端|偵錯項目端|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer 類別<br /><br /> IDialogVisualizerService 介面|資料物件|  
|物件提供者 (實作 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|物件來源 (衍生自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 物件提供者會將要視覺化的物件資料提供給視覺化檢視 UI。 物件提供者是從物件來源處取得物件資料。 物件提供者和物件來源會提供 API，讓偵錯工具端和偵錯項目端之間能夠溝通物件資料。  
  
 每個視覺化檢視必須取得要視覺化的資料物件。 下表顯示物件提供者和物件來源在這個用途上對應的 API：  
  
|物件提供者|物件來源|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> -或-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 請注意，物件提供者可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> 兩者之一。 這兩個 API 都會導致對物件來源呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>。 呼叫<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName>填入 [System.IO.Stream] (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->)，代表所視覺化物件的序列化的形式。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> 會將資料還原序列化回物件形式，讓您可以將它顯示在用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 所建立的 UI 中。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> 會以原始 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> 來填入資料，您必須自行將資料還原序列化。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> 的運作方式是先呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> 來取得序列化 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->，然後將資料還原序列化。 若 .NET 未將物件序列化，或需要自訂序列化，請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>。 在這種情況下，您也必須覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> 方法。  
  
 如果您建立的是唯讀的視覺化檢視，則與 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> 之間只要有單向通訊就已足夠。 如果所建立的視覺化檢視支援編輯資料物件，就必須多執行其他動作。 您還必須能夠將資料物件從物件提供者傳送回物件來源。 下表顯示做這個用途的物件提供者和物件來源 API：  
  
|物件提供者|物件來源|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> -或-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 請注意，物件提供者同樣可以使用兩個 API。 資料始終是以 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> 形式從物件提供者傳送到物件來源，但 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> 需要您自行將物件序列化成 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> 會接受您提供的物件，將它序列化成 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->，然後呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> 以將 <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> 傳送到 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>。  
  
 若使用兩個 Replace 方法中的任一個，便會在偵錯項目中建立新的資料物件，以取代所視覺化的物件。 如果要變更原始物件的內容，卻不要取代它，請使用下表所示的其中一個 Transfer 方法。 這些 API 會同時雙向傳輸資料，不會取代所視覺化的物件：  
  
|物件提供者|物件來源|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> -或-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)   
 [逐步解說： 在 C# 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [逐步解說： 在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [逐步解說： 在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [視覺化檢視安全性考量](../debugger/visualizer-security-considerations.md)



