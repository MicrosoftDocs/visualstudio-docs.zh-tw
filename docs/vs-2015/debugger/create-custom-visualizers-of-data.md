---
title: 建立資料的自訂視覺化檢視 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
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
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f890277190b9b4d28873e1fe394abdcd95b8a3a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939526"
---
# <a name="create-custom-visualizers-of-data"></a>建立資料的自訂視覺化檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

視覺化檢視是元件[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]偵錯工具使用者介面。 A*視覺化檢視*建立對話方塊或其他介面來顯示變數或物件的方式，是適用於其資料類型。 例如，HTML 視覺化檢視會解譯 HTML 字串，並在瀏覽視窗中顯示出現的結果，而點陣圖視覺化檢視會解譯點陣圖結構，並顯示其所代表的圖形。 除了檢視資料外，有些視覺化檢視也能讓您修改資料。  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 偵錯工具包含六個標準視覺化檢視。 這些是文字、 HTML、 XML 及 JSON 視覺化檢視，當然也作用於字串物件;WPF 樹狀架構視覺化檢視，來顯示 WPF 物件視覺化樹狀結構; 屬性和資料集視覺化檢視，這適用於資料集、 DataView 和 DataTable 物件。 額外的視覺化檢視未來可能可以從 Microsoft Corporation 下載，且可從協力廠商和社群取得。 此外，您可以自行撰寫視覺化檢視，並將它們安裝至 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 偵錯工具中。  
  
> [!NOTE]
>  在 **存放區**應用程式，僅限標準的文字，支援 HTML、 XML 及 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
 偵錯工具中的視覺化檢視是以放大鏡圖示表示。 當您看到的放大鏡圖示**DataTip**、 在偵錯工具變數視窗中，或在**快速監看式** 對話方塊中，您可以按一下放大鏡可選取適用於資料類型的視覺化檢視對應的物件。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
>  偵錯工具視覺化檢視需要比部分信任應用程式所允許還要大的權限。 因此，當您在部分信任的程式碼中被停止時，視覺化檢視將不會載入。 若要使用視覺化檢視進行偵錯，您必須以完全信任方式執行程式碼。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)  
  
 [逐步解說：使用 C# 撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：對視覺化檢視進行測試和偵錯](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>相關章節  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
