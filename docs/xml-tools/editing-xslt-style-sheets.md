---
title: 編輯 XSLT 樣式表
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f224e91f72d2fa751ddc8b170f78b8859c43f4
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548446"
---
# <a name="edit-xslt-style-sheets"></a>編輯 XSLT 樣式表

XML 編輯器還可用於編輯 XSLT 樣式表。 您可利用預設的編輯器功能，如 IntelliSense、大綱、XML 片段等。 此外，還有可讓您在 XSLT 中更輕鬆地進行開發的新功能。

## <a name="xslt-features"></a>XSLT 功能
 下表說明使用 XSLT 樣式表的特定功能。

 **語法著色**

 XSLT 關鍵字，例如`template`， `match`，依此類推，會顯示在指定的 XSLT 關鍵字色彩**字型和色彩**設定。

 **波浪底線**

 XML 編輯器使用已安裝*xslt.xsd*檔案來驗證 XSLT 樣式表。 驗證錯誤以藍色波浪底線顯示。 XML 編輯器還會在背景中編譯樣式表，並以適當的波浪底線報告編譯器錯誤或警告。

 **指令碼區塊的支援**

 XSLT 偵錯工具支援指令碼區塊中的程式碼，所以您可以設定中斷點，並逐步執行指令碼區塊程式碼。

 **檢視 XSLT 輸出**

 您可以執行 XSL 轉換，並檢閱 XML 編輯器的輸出。 如需詳細資訊，請參閱[How to： 從 XML 編輯器執行 XSLT 轉換](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)。

 **偵錯 XSLT**

 您可以從 XML 編輯器中的 XSLT 檔案，啟動 XSLT 偵錯工具。 偵錯工具支援在 XSLT 檔案中設定中斷點、檢視 XSLT 執行狀態等。 停留在 XSLT 變數上，即會出現具有變數值的工具提示。 偵錯工具可用於偵錯樣式表，或偵錯從另一個應用程式叫用的已編譯 XSL 轉換。 如需詳細資訊，請參閱[偵錯 XSLT](../xml-tools/debugging-xslt.md)。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)