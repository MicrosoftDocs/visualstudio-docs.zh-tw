---
title: 將 XSLT 程式碼進行偵錯工具的方式
ms.date: 03/05/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bb358efb711211d58525afb8d30d5cb4cad6b2e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646077"
---
# <a name="debugging-xslt"></a>偵錯 XSLT

您可以在 Visual Studio 中，對 XSLT 程式碼進行偵錯工具。 XSLT 偵錯工具支援設定中斷點、查看 XSLT 執行狀態等。 XSLT 偵錯工具可用來調試 XSLT 樣式表單或 XSLT 應用程式。

您可以在程式碼中逐步執行、不進入或跳出，一次執行一行程式碼。 使用 XSLT 偵錯工具之程式碼逐步執行功能的命令，與其他 Visual Studio 偵錯工具的命令相同。

開始偵錯後，XSLT 偵錯工具會開啟視窗，以顯示輸入文件與 XSLT 輸出。

> [!NOTE]
> XSLT 偵錯工具僅適用于 Professional 和 Enterprise 版本的 Visual Studio。

## <a name="debug-from-the-xml-editor"></a>從 XML 編輯器進行 Debug

當您在編輯器中開啟樣式表單或輸入 XML 檔案時，可以啟動偵錯工具。 這可讓您在設計樣式表單時進行 debug。

1. 在 Visual Studio 中開啟樣式表單或 XML 檔案。

1. 從 [ **XML** ] 功能表中選取 [**啟動 XSLT 調試**]，或按**Alt** +**F5**。

## <a name="debug-from-an-app-that-uses-xslt"></a>從使用 XSLT 的應用程式進行 Debug

您可以在偵錯工具時逐步執行 XSLT。 當您在 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 呼叫上按**F11**鍵時，偵錯工具可以逐步執行 XSLT 程式碼。

> [!NOTE]
> 不支援從 <xref:System.Xml.Xsl.XslTransform> 類別逐步執行 XSLT。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別是在偵錯時，唯一支援逐步執行 XSLT 的 XSLT 處理器。

### <a name="to-start-debugging-an-xslt-application"></a>開始偵錯 XSLT 應用程式

1. 當具現化 <xref:System.Xml.Xsl.XslCompiledTransform> 物件時，請在程式碼中將 `enableDebug` 參數設為 `true`。 這可在編譯程式碼時，告訴 XSLT 處理器建立偵錯資訊。

1. 按**F11**逐步執行 XSLT 程式碼。

   XSLT 樣式表單會在新的文件視窗中載入，而且 XSLT 偵錯工具會啟動。

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
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT 分析工具

[Xslt](../xml-tools/xslt-profiler.md)分析工具可讓開發人員建立詳細的 xslt 效能報告，以測量、評估和鎖定 XSLT 程式碼中與效能相關的問題。 如需詳細資訊，請參閱[XSLT profiler](../xml-tools/xslt-profiler.md)。

## <a name="see-also"></a>請參閱

- [逐步解說： Debug XSLT 樣式表單](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [第一次查看 Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)
- [調試基本概念：中斷點](../debugger/using-breakpoints.md)
