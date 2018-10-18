---
title: 如何： 撰寫視覺化檢視 |Microsoft Docs
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815c2eba06af4fe50eb9dc87dd158fe1713342ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280146"
---
# <a name="how-to-write-a-visualizer"></a>如何：撰寫視覺化檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以為任何 Managed 類別的物件撰寫自訂視覺化檢視，除了 <xref:System.Object> 或 <xref:System.Array> 以外。  
  
> [!NOTE]
>  在 **存放區**應用程式，僅限標準的文字，支援 HTML、 XML 及 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
 偵錯工具視覺化檢視的架構分為兩部分：  
  
-   *偵錯工具端*Visual Studio 偵錯工具內執行。 偵錯工具端的程式碼會建立並顯示視覺化檢視的使用者介面。  
  
-   *偵錯項目端*Visual Studio 偵錯處理序內執行 (*偵錯項目*)。  
  
 您要進行視覺化的資料物件 (例如，String 物件) 會存在於偵錯項目處理序中。 因此，偵錯項目端必須將該資料物件傳送至偵錯工具端，然後偵錯工具端才能使用您建立的使用者介面顯示這個資料物件。  
  
 偵錯工具端會接收要視覺化從這個資料物件*物件提供者*可實<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>介面。 在偵錯項目端傳送的資料物件，可透過*物件來源*，其係衍生自<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>。 物件提供者也可以將資料送回物件來源，以便您撰寫可編輯和顯示資料的視覺化檢視。 物件提供者可被覆寫，以便與運算式評估工具進行溝通，也就是與物件來源溝通。  
  
 偵錯項目端和偵錯工具端是透過 <xref:System.IO.Stream> 相互溝通。 提供的方法是用來將資料物件序列化至 <xref:System.IO.Stream>，並將 <xref:System.IO.Stream> 還原序列化至資料物件中。  
  
 偵錯項目端的程式碼是使用 DebuggerVisualizer 屬性 (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) 進行指定。  
  
 若要在偵錯工具端建立視覺化檢視使用者介面，您必須建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別，並覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法顯示此介面。  
  
 您可以使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>，從您的視覺化檢視顯示 Windows Form、對話方塊和控制項。  
  
 對泛型類型的支援是有限的。 只有在泛型類型是開啟類型時，才能夠為泛型類型目標撰寫視覺化檢視。 這項限制與使用 `DebuggerTypeProxy` 屬性時的限制相同。 如需詳細資訊，請參閱 <<c0> [ 使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)。  
  
 自訂視覺化檢視會有安全性考量。 請參閱[視覺化檢視安全性考量](../debugger/visualizer-security-considerations.md)。  
  
 下列程序提供在建立視覺化檢視時所需的概觀。 如需詳細的說明，請參閱[逐步解說： 在 C# 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。  
  
### <a name="to-create-the-debugger-side"></a>若要建立偵錯工具端  
  
1.  請使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 方法，取得偵錯工具端的視覺化物件。  
  
2.  建立繼承自 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 的類別。  
  
3.  覆寫 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 方法以顯示介面。 使用 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 方法以將 Windows Form、對話方塊和控制項顯示為介面的一部分。  
  
4.  套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，並賦予它一個視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>若要建立偵錯項目端  
  
1.  套用 <xref:System.Diagnostics.DebuggerVisualizerAttribute>，並賦予它一個視覺化檢視 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) 和物件來源 (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)。 如果您忽略了物件來源，將使用預設的物件來源。  
  
2.  如果您希望視覺化檢視能夠編輯和顯示資料物件，您必須從 `TransferData` 覆寫 `CreateReplacementObject` 或 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 方法。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [如何： 測試和偵錯視覺化檢視](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [視覺化檢視安全性考量](../debugger/visualizer-security-considerations.md)



