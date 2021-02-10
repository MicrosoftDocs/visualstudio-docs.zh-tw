---
title: XSLT 代碼的調試方式
description: 瞭解如何使用 XSLT 偵錯工具，逐步執行程式碼、設定中斷點和查看 XSLT 執行狀態，以在 Visual Studio 中將 XSLT 程式碼進行偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a7d0f5a683a627999076969dbc9077ba03d65208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948553"
---
# <a name="debugging-xslt"></a>偵錯 XSLT

您可以在 Visual Studio 中進行 XSLT 程式碼的偵錯工具。 XSLT 偵錯工具支援設定中斷點、查看 XSLT 執行狀態等。 XSLT 偵錯工具可以用來將 XSLT 樣式表單或 XSLT 應用程式進行偵錯工具。

您可以逐步執行、逐步執行程式碼或逐步執行程式碼，一次執行一行程式碼。 使用 XSLT 偵錯工具之程式碼逐步執行功能的命令，與其他 Visual Studio 偵錯工具的命令相同。

開始偵錯後，XSLT 偵錯工具會開啟視窗，以顯示輸入文件與 XSLT 輸出。

> [!NOTE]
> XSLT 偵錯工具僅適用于 Visual Studio 的 Professional 和 Enterprise 版本。

## <a name="debug-from-the-xml-editor"></a>從 XML 編輯器進行調試

當您在編輯器中開啟樣式表單或輸入 XML 檔案時，可以啟動偵錯工具。 這可讓您在設計樣式表單時進行 debug。

1. 在 Visual Studio 中開啟樣式表單或 XML 檔案。

1. 從 [ **XML** ] 功能表選取 [**啟動 XSLT 調試**]，或按 **Alt** + **F5**。

## <a name="debug-from-an-app-that-uses-xslt"></a>從使用 XSLT 的應用程式進行偵錯工具

您可以在偵錯工具時逐步執行 XSLT。 當您在呼叫上按 **F11** 時 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> ，偵錯工具可以逐步執行 XSLT 程式碼。

> [!NOTE]
> 不支援從 <xref:System.Xml.Xsl.XslTransform> 類別逐步執行 XSLT。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別是在偵錯時，唯一支援逐步執行 XSLT 的 XSLT 處理器。

### <a name="to-start-debugging-an-xslt-application"></a>開始偵錯 XSLT 應用程式

1. 當具現化 <xref:System.Xml.Xsl.XslCompiledTransform> 物件時，請在程式碼中將 `enableDebug` 參數設為 `true`。 這可在編譯程式碼時，告訴 XSLT 處理器建立偵錯資訊。

1. 按 **F11** 以逐步執行 XSLT 程式碼。

   XSLT 樣式表單會載入到新的文件視窗中，並啟動 XSLT 偵錯工具。

   或者，您也可以將中斷點加入至樣式表，然後執行應用程式。

### <a name="example"></a>範例

下面是 C# XSLT 程式的範例。 它顯示如何啟用 XSLT 偵錯。

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT 分析工具

[Xslt](../xml-tools/xslt-profiler.md)分析工具是一種工具，可讓開發人員藉由建立詳細的 xslt 效能報告，來測量、評估及鎖定 XSLT 程式碼中的效能相關問題。 如需詳細資訊，請參閱 [XSLT profiler](../xml-tools/xslt-profiler.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [先查看 Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)
- [調試基本概念：中斷點](../debugger/using-breakpoints.md)
