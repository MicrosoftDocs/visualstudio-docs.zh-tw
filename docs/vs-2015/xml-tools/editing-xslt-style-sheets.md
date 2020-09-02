---
title: 編輯 XSLT 樣式表單 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670960"
---
# <a name="editing-xslt-style-sheets"></a>編輯 XSLT 樣式表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器還可用於編輯 XSLT 樣式表。 您可利用預設的編輯器功能，如 IntelliSense、大綱、XML 片段等。 此外，還有可讓您在 XSLT 中更輕鬆地進行開發的新功能。

## <a name="xslt-features"></a>XSLT 功能
 下表說明使用 XSLT 樣式表的特定功能。

 **語法著色** XSLT 關鍵字（例如 `template` 、 `match` 等）會以 [字型] **和 [色彩** ] 設定所指定的 xslt 關鍵字色彩顯示。

 **波浪** 底線XML 編輯器會使用已安裝的 xslt .xsd 檔案來驗證 XSLT 樣式表單。 驗證錯誤以藍色波浪底線顯示。 XML 編輯器還會在背景中編譯樣式表，並以適當的波浪底線報告編譯器錯誤或警告。

 **支援腳本區塊** XSLT 偵錯工具支援腳本區塊中的程式碼，因此您可以設定中斷點，並逐步執行腳本區塊程式碼。

 **查看 XSLT 輸出** 您可以執行 XSL 轉換並查看 XML 編輯器的輸出。 如需詳細資訊，請參閱 [如何：從 XML 編輯器執行 XSLT 轉換](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)。

 **調試 XSLT** 您可以從 XML 編輯器中的 XSLT 檔案啟動 XSLT 偵錯工具。 偵錯工具支援在 XSLT 檔案中設定中斷點、檢視 XSLT 執行狀態等。 停留在 XSLT 變數上，即會出現具有變數值的工具提示。 偵錯工具可用於偵錯樣式表，或偵錯從另一個應用程式叫用的已編譯 XSL 轉換。 如需詳細資訊，請參閱 [偵錯工具 XSLT](../xml-tools/debugging-xslt.md)。

## <a name="see-also"></a>另請參閱
 [XML 編輯器](../xml-tools/xml-editor.md)
