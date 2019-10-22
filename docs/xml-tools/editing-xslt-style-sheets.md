---
title: 編輯 XSLT 樣式表
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc987f8362d5daf435b7e9de860cc13f16a1aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646063"
---
# <a name="edit-xslt-style-sheets"></a>編輯 XSLT 樣式表

XML 編輯器也可以用來編輯 XSLT 樣式表單。 您可利用預設的編輯器功能，如 IntelliSense、大綱、XML 片段等。 此外，還有可讓您在 XSLT 中更輕鬆地進行開發的新功能。

## <a name="xslt-features"></a>XSLT 功能

下表說明使用 XSLT 樣式表的特定功能。

**語法著色**

XSLT 關鍵字（例如 `template` 和 `match`）會以 [字型]**和 [色彩**] 設定所指定的 xslt 關鍵字色彩顯示。

**波浪底線**

XML 編輯器會使用已安裝的*xslt .xsd*檔案來驗證 xslt 樣式表單。 驗證錯誤以藍色波浪底線顯示。 XML 編輯器也會在背景中編譯樣式表單，並報告具有適當波浪底線的編譯器錯誤或警告。

**腳本區塊的支援**

XSLT 偵錯工具支援指令碼區塊中的程式碼，所以您可以設定中斷點，並逐步執行指令碼區塊程式碼。

**查看 XSLT 輸出**

您可以執行 XSL 轉換，並從 XML 編輯器中查看輸出。 如需詳細資訊，請參閱[如何：從 XML 編輯器執行 XSLT 轉換](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)。

**Debug XSLT**

您可以從 XML 編輯器中的 XSLT 檔案啟動 XSLT 偵錯工具。 偵錯工具支援在 XSLT 檔案中設定中斷點、檢視 XSLT 執行狀態等。 停留在 XSLT 變數上，即會出現具有變數值的工具提示。 偵錯工具可用於偵錯樣式表，或偵錯從另一個應用程式叫用的已編譯 XSL 轉換。 如需詳細資訊，請參閱[偵錯工具 XSLT](../xml-tools/debugging-xslt.md)。

## <a name="see-also"></a>請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)