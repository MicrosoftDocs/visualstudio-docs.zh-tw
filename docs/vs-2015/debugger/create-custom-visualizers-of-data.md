---
title: 建立資料的自訂視覺化 |Microsoft Docs
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
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839117"
---
# <a name="create-custom-visualizers-of-data"></a>建立資料的自訂視覺化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

視覺化 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 程式是偵錯工具使用者介面的元件。 *視覺化*程式會建立一個對話方塊或另一個介面，以適用于其資料類型的方式來顯示變數或物件。 例如，HTML 視覺化檢視會解譯 HTML 字串，並在瀏覽視窗中顯示出現的結果，而點陣圖視覺化檢視會解譯點陣圖結構，並顯示其所代表的圖形。 除了檢視資料外，有些視覺化檢視也能讓您修改資料。  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 偵錯工具包含六個標準視覺化檢視。 它們分別為文字、HTML、XML 及 JSON 視覺化檢閱、WPF 樹狀架構視覺化檢閱和資料集視覺化檢閱。前三者適用於字串物件，WPF 樹狀架構視化檢閱可用來顯示 WPF 物件視覺化樹狀，而資料集視覺化檢閱則適用於資料集、DataView 和 DataTable 物件。 額外的視覺化檢視未來可能可以從 Microsoft Corporation 下載，且可從協力廠商和社群取得。 此外，您可以自行撰寫視覺化檢視，並將它們安裝至 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 偵錯工具中。  
  
> [!NOTE]
> 在 **Store** 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
 偵錯工具中的視覺化檢視是以放大鏡圖示表示。 當您在 [ **資料提示**]、[偵錯工具變數] 視窗或 [ **快速** 監看式] 對話方塊中看到放大鏡圖示時，可以按一下放大鏡來選取適合對應物件之資料類型的視覺化檢視。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
> 偵錯工具視覺化檢視需要比部分信任應用程式所允許還要大的權限。 因此，當您在部分信任的程式碼中被停止時，視覺化檢視將不會載入。 若要使用視覺化檢視進行偵錯，您必須以完全信任方式執行程式碼。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)  
  
 [逐步解說：以 C 撰寫視覺化#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：測試和偵測視覺化視覺化](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>相關章節  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
