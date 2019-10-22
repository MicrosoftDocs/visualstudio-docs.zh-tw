---
title: XML 文件屬性 (屬性視窗)
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99102248a9456de3a2b3aeba28e54de4299fae40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604149"
---
# <a name="xml-document-properties-properties-window"></a>XML 文件屬性，屬性視窗

[**屬性**] 視窗提供 XML 編輯器中作用中檔的基本資訊。 可用的屬性視目前使用中 XML 文件的型別而定。

> [!NOTE]
> 所有 XML 文件屬性都儲存在解決方案中。 因此，在下次開啟解決方案時無需重新輸入這些值。

**編碼**

檔案的字元編碼。 變更此屬性，亦會變更 XML 宣告上的編碼屬性，反之亦然。 當您儲存檔案時，會使用新的編碼方式將檔案編碼。

**輸入**

與 XSLT 樣式表相關聯的輸入文件。 **啟動 xslt**命令會使用它，例如， **XML**  >  在不進行偵錯工具的情況下**啟動 xslt**。 您可以使用 [流覽] （ **...** ）按鈕來選取檔。

只有在編輯器中開啟 XSLT 檔案時，才會顯示這個屬性。

**Output**

轉換 XML 文件時所產生的檔案。

如果未指定檔案，就會根據 `xsl:output` 元素上的 `method` 屬性來產生預設檔案名，這會決定副檔名。 預設檔案位於目前使用者的暫存目錄中。

**結構描述**

用於驗證的結構描述。 此按鈕會開啟 [ **XSD 架構**] 對話方塊，可用於選取要使用的架構。

亦可輸入結構描述的路徑。 如果指定多個結構描述，則每個結構描述路徑都必須包含在雙引號中。

**樣式表單**

使用 XSLT 檔案，用於在沒有偵錯工具的情況下**啟動 Xslt 調試**程式和**啟動 xslt**時轉換檔。 如果此欄位為空白，則編輯器會使用檔之 `xml-stylesheet` 處理指示中提供的值，或提示您輸入檔案名。

當您編輯 XSLT 檔案時，可以使用這個屬性來指定當選取 [**啟動 Xslt 調試**程式] 或 [**啟動 xslt 但不進行調試**程式] 命令時，應該使用不同的樣式表單。 例如，當您編輯的樣式表單包含在父樣式表單中時，您可能會想要這麼做。

## <a name="see-also"></a>請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)