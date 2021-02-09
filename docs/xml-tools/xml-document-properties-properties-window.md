---
title: XML 文件屬性 (屬性視窗)
description: 瞭解屬性視窗中的 XML 文件屬性，以提供 XML 編輯器中使用中檔的基本資訊。
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e12118f2f7f5d9189ca768f7be65a35b490eb54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875012"
---
# <a name="xml-document-properties-properties-window"></a>XML 文件屬性，屬性視窗

[ **屬性** ] 視窗提供在 XML 編輯器中作用中檔的基本資訊。 可用的屬性視目前使用中 XML 文件的型別而定。

> [!NOTE]
> 所有 XML 文件屬性都儲存在解決方案中。 因此，在下次開啟解決方案時無需重新輸入這些值。

**編碼方式**

檔案的字元編碼。 變更此屬性，亦會變更 XML 宣告上的編碼屬性，反之亦然。 當您儲存檔案時，會使用新的編碼來編碼檔案。

**輸入**

與 XSLT 樣式表相關聯的輸入文件。 它是由 **啟動 xslt** 命令使用，例如， **XML**  >  **啟動 xslt 而不進行調試**。 您可以使用 [ **流覽 (]**) 按鈕來選取檔。

只有在編輯器中開啟 XSLT 檔案時，才會顯示此屬性。

**輸出**

轉換 XML 文件時所產生的檔案。

如果未指定檔案，則會根據 `method` 元素上的屬性 `xsl:output` （可決定副檔名）來產生預設檔案名。 預設檔案位於目前使用者的暫存目錄中。

**結構描述**

用於驗證的結構描述。 此按鈕會開啟 [ **XSD 架構** ] 對話方塊，可用來選取要使用的架構。

亦可輸入結構描述的路徑。 如果指定多個結構描述，則每個結構描述路徑都必須包含在雙引號中。

**樣式 表**

使用 XSLT 檔，用來在 **啟動 Xslt 調試** 程式並啟動 xslt 時（ **不含調試** 程式命令）使用轉換檔。 如果這個欄位是空白的，則編輯器會使用檔處理指示中所提供的值， `xml-stylesheet` 或提示您輸入檔案名。

編輯 XSLT 檔案時，這個屬性可用來指定當選取 [ **啟動 Xslt 調試** 程式或 **啟動 xslt 但不使用調試** 程式] 命令時，應該使用不同的樣式表單。 例如，當您編輯的樣式表單包含在父樣式表單中時，您可能會想要這樣做。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
