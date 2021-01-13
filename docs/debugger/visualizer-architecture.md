---
title: 視覺化架構 |Microsoft Docs
description: 視覺化檢視會顯示特定類型的資料元素，而且可能也會允許編輯。 瞭解視覺化檢視的架構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9166cc3c98f72e43042a26c0787d1cbf45223a74
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149751"
---
# <a name="visualizer-architecture"></a>視覺化檢視架構
偵錯工具視覺化檢視的架構分為兩部分：

- 「偵錯工具端」(*debugger side*) 會在 Visual Studio 偵錯工具中執行。 偵錯工具端的程式碼會建立並顯示視覺化檢視的使用者介面。

- 「偵錯項目端」會在 Visual Studio 正在偵錯的處理序 (亦即「偵錯項目」) 中執行。

  視覺化檢視是偵錯工具的一個元件，它讓偵錯工具可以用有意義、容易了解的形式，顯示 (「視覺化」(*visualize*)) 資料物件的內容。 有些視覺化檢視也支援編輯資料物件。 您可以撰寫自訂的視覺化檢視，來將偵錯工具擴充成可以處理自己的自訂資料型別。

  要視覺化的資料物件位於所偵錯的處理序 (「偵錯項目」處理序) 內。 即將顯示資料的使用者介面則在 Visual Studio 偵錯工具處理序內建立：

|偵錯工具處理序|偵錯項目處理序|
|----------------------|----------------------|
|偵錯工具使用者介面 (資料提示方塊、監看式視窗、快速監看式)|要視覺化的資料物件|

 若要在偵錯工具介面中將資料物件視覺化，您必須編寫兩個處理序之間的通訊程式碼。 因此，視覺化檢視架構分為兩部分：「偵錯工具端」程式碼和「偵錯項目端」程式碼。

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
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> – 或 –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 請注意，物件提供者可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> 兩者之一。 這兩個 API 都會導致對物件來源呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>。 呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> 會填入 <xref:System.IO.Stream?displayProperty=fullName>，以代表所視覺化物件的序列化形式。

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> 會將資料還原序列化回物件格式，且可將其顯示於您使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 建立的 UI 中。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> 會將資料填入為原始 `Stream`，您必須自行予以還原序列化。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> 透過呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> 來運作，以取得序列化的 `Stream`，接著將資料還原序列化。 若 .NET 未將物件序列化，或需要自訂序列化，請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>。 在這種情況下，您也必須覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> 方法。

 如果您建立的是唯讀的視覺化檢視，則與 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> 之間只要有單向通訊就已足夠。 如果所建立的視覺化檢視支援編輯資料物件，就必須多執行其他動作。 您還必須能夠將資料物件從物件提供者傳送回物件來源。 下表顯示做這個用途的物件提供者和物件來源 API：

|物件提供者|物件來源|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> – 或 –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 請注意，物件提供者同樣可以使用兩個 API。 資料始終是以 `Stream` 形式從物件提供者傳送到物件來源，但 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> 需要您自行將物件序列化成 `Stream`。

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> 會利用您提供的物件，將其序列化為 `Stream`，接著呼叫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> 以將 `Stream` 傳送至 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>。

 若使用兩個 Replace 方法中的任一個，便會在偵錯項目中建立新的資料物件，以取代所視覺化的物件。 如果要變更原始物件的內容，卻不要取代它，請使用下表所示的其中一個 Transfer 方法。 這些 API 會同時雙向傳輸資料，不會取代所視覺化的物件：

|物件提供者|物件來源|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> – 或 –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>另請參閱
- [如何：撰寫視覺化檢視](create-custom-visualizers-of-data.md)
- [逐步解說：以 C 撰寫視覺化#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [逐步解說：在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [逐步解說：在 Visual Basic 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [視覺化檢視安全性考慮](../debugger/visualizer-security-considerations.md)