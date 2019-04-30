---
title: 若要偵錯 XSLT 程式碼的方式
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 23e108e476bfa9cb3ce699a16c77eb3520ed4785
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838476"
---
# <a name="debugging-xslt"></a>偵錯 XSLT

您可以偵錯在 Visual Studio 中的 XSLT 程式碼。 XSLT 偵錯工具設定中斷點、 檢視 XSLT 執行狀態的支援等等。 XSLT 偵錯工具可用來偵錯 XSLT 樣式表或 XSLT 應用程式。

您可以一次執行一行程式碼，藉由逐步執行、 跨過或跳出程式碼。 使用 XSLT 偵錯工具的程式碼逐步偵錯功能的命令是相同的其他 Visual Studio 偵錯工具。

開始偵錯後，XSLT 偵錯工具會開啟視窗，以顯示輸入文件與 XSLT 輸出。

> [!NOTE]
> 只有 Enterprise 版的 Visual Studio 中使用 XSLT 偵錯工具。

## <a name="debug-from-the-xml-editor"></a>從 XML 編輯器進行偵錯

在樣式表或輸入的 XML 檔案在編輯器中開啟時，您就可以開始偵錯工具。 這可讓您進行偵錯，當您在設計樣式表。

1. 在 Visual Studio 中開啟樣式表或 XML 檔案。

1. 選取 **啟動 XSLT 偵錯**從**XML**功能表或按下**Alt**+**F5**。

## <a name="debug-from-an-app-that-uses-xslt"></a>從使用 XSLT 的應用程式偵錯

偵錯應用程式時，您可以逐步執行 XSLT。 當您按下**F11**上<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>呼叫，偵錯工具可以逐步執行 XSLT 程式碼。

> [!NOTE]
> 不支援從 <xref:System.Xml.Xsl.XslTransform> 類別逐步執行 XSLT。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別是在偵錯時，唯一支援逐步執行 XSLT 的 XSLT 處理器。

### <a name="to-start-debugging-an-xslt-application"></a>開始偵錯 XSLT 應用程式

1. 當具現化 <xref:System.Xml.Xsl.XslCompiledTransform> 物件時，請在程式碼中將 `enableDebug` 參數設為 `true`。 這可在編譯程式碼時，告訴 XSLT 處理器建立偵錯資訊。

1. 按下**F11**逐步執行 XSLT 程式碼。

   在新的文件視窗中載入 XSLT 樣式表，並啟動 XSLT 偵錯工具。

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

[XSLT 分析工具](../xml-tools/xslt-profiler.md)是一種工具，可讓開發人員測量、 評估及鎖定 XSLT 程式碼中的效能相關問題，方法是建立詳細的 XSLT 效能報告。 如需詳細資訊，請參閱 < [XSLT 分析工具](../xml-tools/xslt-profiler.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [搶先了解 Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)
- [偵錯基本概念：中斷點](../debugger/using-breakpoints.md)