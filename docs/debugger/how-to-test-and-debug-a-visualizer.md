---
title: 測試和偵測視覺化檢視 |Microsoft Docs
description: 藉由從測試驅動程式 (視覺化程式開發主機) 或在 Visual Studio 中安裝並從偵錯工具視窗呼叫，來測試和偵測視覺化檢視。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b01c97c0ee72a3d29052d98d8a37cdc746c26d27
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923278"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>如何：測試和偵錯視覺化檢視
當您撰寫完視覺化檢視之後，必須對其進行偵錯和測試。

測試視覺化檢視的其中一種方法，是將它安裝在 Visual Studio，並從偵錯工具視窗中呼叫它   (請參閱 [如何：安裝視覺化](../debugger/how-to-install-a-visualizer.md)程式。 ) 如果這樣做，您將需要使用 Visual Studio 的第二個實例來附加和偵測在偵錯工具的第一個實例中執行的視覺化檢視。

對視覺化檢視進行偵錯的簡單方法，是從測試驅動程式中執行該視覺化檢視。 視覺化檢視的 API 能夠輕易建立這種驅動程式，也就是所謂的「視覺化檢視開發主應用程式」。

### <a name="to-create-a-visualizer-development-host"></a>若要建立視覺化檢視開發主應用程式

1. 在偵錯工具端的類別中，包含建立 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> 物件和呼叫其 Show 方法的靜態方法：

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    用來建構這個主應用程式的參數，是要顯示在視覺化檢視 (`objectToVisualize`) 中的資料物件，以及偵錯工具旁邊的類別類型。

2. 加入下列陳述式呼叫 `TestShowVisualizer`。 如果您在類別庫 (Class Library) 中建立視覺化檢視，必須建立一個可執行檔呼叫這個類別庫，並將這個陳述式放置在可執行檔中：

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    如需更完整的範例，請參閱 [逐步解說：在 c # 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)。

## <a name="see-also"></a>另請參閱
- [逐步解說：以 C 撰寫視覺化#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
