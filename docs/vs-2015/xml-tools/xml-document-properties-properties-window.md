---
title: XML 文件屬性，屬性視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4b1441ef6547fe955734fd7556b27a08781461c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660654"
---
# <a name="xml-document-properties-properties-window"></a>XML 文件屬性 (屬性視窗)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**屬性**視窗提供中文件的 XML 編輯器中的基本資訊。 可用的屬性視目前使用中 XML 文件的型別而定。  
  
> [!NOTE]
>  所有 XML 文件屬性都儲存在解決方案中。 因此，在下次開啟解決方案時無需重新輸入這些值。  
  
 **編碼方式**  
 檔案的字元編碼。 變更此屬性，亦會變更 XML 宣告上的編碼屬性，反之亦然。 儲存檔案時，新的編碼將用於對檔案進行編碼。  
  
 **輸入**  
 與 XSLT 樣式表相關聯的輸入文件。 它由**ShowXSLT 輸出**命令。 可以使用 瀏覽 選取文件 (**...**) 按鈕。  
  
 僅當 [編輯器] 視窗中有目前使用中的 XSLT 檔案時，才可看到此屬性。  
  
 **輸出**  
 轉換 XML 文件時所產生的檔案。  
  
 如果未指定檔案，則會依據決定副檔名之 `method` 項目上的 `xsl:output` 屬性，產生預設檔名。 預設檔案位於目前使用者的暫存目錄中。  
  
 **結構描述**  
 用於驗證的結構描述。 按鈕會開啟**XSD 結構描述**對話方塊中，可用來選取要使用的結構描述。  
  
 亦可輸入結構描述的路徑。 如果指定多個結構描述，則每個結構描述路徑都必須包含在雙引號中。  
  
 **Stylesheet**  
 用來轉換文件的 XSLT 檔案時**顯示 XSLT 輸出**命令可用。 如果此欄位為空白時**顯示 XSLT 輸出**命令時，編輯器使用中提供的值`xml-stylesheet`處理指示的文件，它會提示您輸入檔案名稱。  
  
 編輯 XSLT 檔案時，此屬性可用來指定不同的樣式表應使用的時機**顯示 XSLT 輸出**或**偵錯 XSLT**選取命令時。 例如，當編輯包含在父樣式表中的樣式表時，您可能想要這樣做。  
  
## <a name="see-also"></a>另請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)   
 [XML 編輯器元件](../xml-tools/xml-editor-components.md)
