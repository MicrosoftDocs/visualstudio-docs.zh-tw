---
title: XML 文件屬性 (屬性視窗)
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526265"
---
# <a name="xml-document-properties-properties-window"></a>屬性視窗、 XML 文件屬性

**屬性**視窗會提供在 XML 編輯器中的文件的基本資訊。 可用的屬性視目前使用中 XML 文件的型別而定。

> [!NOTE]
> 所有 XML 文件屬性都儲存在解決方案中。 因此，在下次開啟解決方案時無需重新輸入這些值。

**編碼方式**

檔案的字元編碼。 變更此屬性，亦會變更 XML 宣告上的編碼屬性，反之亦然。 新的編碼方式，用來儲存檔案時，將檔案的編碼。

**輸入**

與 XSLT 樣式表相關聯的輸入文件。 它由**啟動 XSLT**命令，例如**XML** > **啟動 XSLT 但不偵錯**。 可以使用 瀏覽 選取文件 (**...**) 按鈕。

只有在編輯器中開啟 XSLT 檔時，只顯示這個屬性。

**輸出**

轉換 XML 文件時所產生的檔案。

如果未指定檔案，預設的檔案名稱根據產生`method`屬性上`xsl:output`元素，其決定副檔名。 預設檔案位於目前使用者的暫存目錄中。

**結構描述**

用於驗證的結構描述。 按鈕會開啟**XSD 結構描述**對話方塊中，可用來選取要使用的結構描述。

亦可輸入結構描述的路徑。 如果指定多個結構描述，則每個結構描述路徑都必須包含在雙引號中。

**Stylesheet**

用來轉換文件的 XSLT 檔案時**啟動 XSLT 偵錯**並**啟動 XSLT 但不偵錯**命令可用。 這個欄位是空白的如果編輯器使用中提供的值`xml-stylesheet`處理指示的文件，或者它會提示您輸入檔案名稱。

編輯 XSLT 檔案時，此屬性可用來指定不同的樣式表應使用的時機**啟動 XSLT 偵錯**或**啟動 XSLT 但不偵錯**選取命令時。 例如，您可能要這樣做，當您編輯包含在父樣式表中的樣式表。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)