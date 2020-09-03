---
title: How to：啟動調試 XSLT |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656336"
---
# <a name="how-to-start-debugging-xslt"></a>HOW TO：開始偵錯 XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT 偵錯工具可用於偵錯 XSLT 樣式表或 XSLT 應用程式。 偵錯時，您可藉由逐步執行、跨過或跳出程式碼，來逐行執行程式碼。 XSLT 偵錯工具使用程式碼逐步執行功能的命令，與其他 Visual Studio 偵錯工具用法相同。 開始偵錯後，XSLT 偵錯工具會開啟視窗，以顯示輸入文件與 XSLT 輸出。

## <a name="xml-editor"></a>XML 編輯器
 您可以從 XML 編輯器啟動偵錯工具。 這可讓您在設計樣式表時進行偵錯。

#### <a name="to-start-debugging-from-a-style-sheet"></a>若要從樣式表開始偵錯

1. 在 [XML 編輯器] 中開啟樣式表。

2. 從 [ **XML** ] 功能表選取 [ **Debug XSL** ]。

#### <a name="to-start-debugging-from-an-xml-input-document"></a>若要從 XML 輸入文件開始偵錯

1. 在 XML 編輯器中開啟 XML 文件。

2. 從 [ **XML** ] 功能表選取 [ **Debug XSL** ]。

## <a name="xslt-from-other-languages"></a>其他語言的 XSLT
 您還可在偵錯應用程式時逐步執行 XSLT。 當您在 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 呼叫上按 F11 時，偵錯工具可逐步執行 XSLT 程式碼。

> [!NOTE]
> 不支援從 <xref:System.Xml.Xsl.XslTransform> 類別逐步執行 XSLT。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別是在偵錯時，唯一支援逐步執行 XSLT 的 XSLT 處理器。

#### <a name="to-start-debugging-an-xslt-application"></a>開始偵錯 XSLT 應用程式

1. 當具現化 <xref:System.Xml.Xsl.XslCompiledTransform> 物件時，請在程式碼中將 `enableDebug` 參數設為 `true`。

     這可在編譯程式碼時，告訴 XSLT 處理器建立偵錯資訊。

2. 按 F11，以逐步執行 XSLT 程式碼。

     新文件視窗中會載入 XSLT 樣式表，並啟動 XSLT 偵錯工具。

     或者，您也可以將中斷點加入至樣式表，然後執行應用程式。

### <a name="example"></a>範例
 下面是 C# XSLT 程式的範例。 它顯示如何啟用 XSLT 偵錯。

```
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
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

## <a name="see-also"></a>另請參閱
 [逐步解說： DEBUG XSLT 樣式表單程式](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)[代碼逐步執行總覽](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
