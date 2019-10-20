---
title: XML 文件屬性，屬性視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669510"
---
# <a name="xml-document-properties-properties-window"></a>XML 文件屬性 (屬性視窗)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[**屬性**] 視窗提供 XML 編輯器中作用中檔的基本資訊。 可用的屬性視目前使用中 XML 文件的型別而定。

> [!NOTE]
> 所有 XML 文件屬性都儲存在解決方案中。 因此，在下次開啟解決方案時無需重新輸入這些值。

 **編碼**檔案的字元編碼方式。 變更此屬性，亦會變更 XML 宣告上的編碼屬性，反之亦然。 儲存檔案時，新的編碼將用於對檔案進行編碼。

 **輸入**與 XSLT 樣式表單相關聯的輸入檔。 **ShowXSLT Output**命令會使用它。 您可以使用 [流覽] （ **...** ）按鈕來選取檔。

 僅當 [編輯器] 視窗中有目前使用中的 XSLT 檔案時，才可看到此屬性。

 **輸出**轉換 XML 檔時所產生的檔案。

 如果未指定檔案，則會依據決定副檔名之 `method` 項目上的 `xsl:output` 屬性，產生預設檔名。 預設檔案位於目前使用者的暫存目錄中。

 **架構**用於驗證的架構。 此按鈕會開啟 [ **XSD 架構**] 對話方塊，可用於選取要使用的架構。

 亦可輸入結構描述的路徑。 如果指定多個結構描述，則每個結構描述路徑都必須包含在雙引號中。

 **樣式**表單使用 [**顯示 Xslt 輸出**] 命令時，用來轉換檔的 XSLT 檔案。 當使用 [**顯示 XSLT 輸出**] 命令時，如果此欄位為空白，則編輯器會使用檔之 `xml-stylesheet` 處理指示中提供的值，或提示您輸入檔案名。

 編輯 XSLT 檔案時，可以使用這個屬性來指定當選取 [**顯示 Xslt 輸出**] 或 [ **Debug xslt** ] 命令時，應該使用不同的樣式表單。 例如，當編輯包含在父樣式表中的樣式表時，您可能想要這樣做。

## <a name="see-also"></a>請參閱
 [Xml 編輯器](../xml-tools/xml-editor.md) [xml 編輯器元件](../xml-tools/xml-editor-components.md)
