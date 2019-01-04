---
title: HOW TO：從 XML 編輯器執行 XSLT 轉換
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fccad81c2990a93e78f329e2ee4af070d6e5c97
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866513"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>HOW TO：從 XML 編輯器執行 XSLT 轉換

XML 編輯器可讓您將 XSLT 樣式表與 XML 文件相關聯、執行轉換，以及檢閱輸出。 XSLT 轉換的結果輸出會顯示在新文件視窗中。

**輸出**屬性指定輸出的檔案名稱。 如果**輸出**屬性為空白，就會產生檔名，暫存目錄中。 副檔名根據`xsl:output`項目，以您的樣式表，而且可以是。*xml*，。*txt*或。*htm*。

如果**輸出**屬性指定的檔名。*htm*或。*html* XSLT 輸出是預覽使用延伸模組， [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer。 所有其他副檔名都使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio 所選擇的預設編輯器來開啟。 例如，如果檔案的副檔名。*xml*，Visual Studio 會使用 XML 編輯器。

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>從 XML 文件執行 XSLT 轉換

1.  在 XML 編輯器中開啟 XML 文件。

2.  將 XSLT 樣式表與 XML 文件產生關聯。

    -   將 `xml-stylesheet` 處理指示加入 XML 文件。 例如，加入下列行 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 至文件初構。

         -或-

    -   加入 XSLT 樣式表 using**屬性**視窗。 在文件**屬性] 視窗**，按一下**瀏覽**按鈕**樣式表**欄位中，選取 XSLT 樣式表，然後按一下 [**開啟**.

3.  按一下  **ShowXSL 輸出**按鈕**XML 編輯器**工具列。

    > [!NOTE]
    > 如果沒有與 XML 文件相關聯的樣式表，則會出現一個對話方塊，提示您提供要使用的樣式表。
    >
    >  XSLT 轉換的結果輸出會顯示在新文件視窗中。

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>從 XSLT 樣式表執行 XSLT 轉換

1.  在 [XML 編輯器] 中開啟 XSLT 樣式表。

2.  指定在 XML 文件**輸入**欄位的文件**屬性**視窗。

    > [!NOTE]
    > XML 文件為用於轉換的輸入文件。 如果啟動 XSLT 轉換時，未指定文件，則**開啟舊檔** 對話方塊隨即出現，而且可以指定文件在該時間。

3.  按一下  **ShowXSLT 輸出**按鈕**XML 編輯器**工具列。

     XSLT 轉換的結果輸出會顯示在新文件視窗中。

## <a name="to-provide-a-different-output-file-name"></a>提供不同的輸出檔案名稱

1.  指定檔案名稱以**輸出**欄位的文件**屬性**視窗。

2.  按一下  **ShowXSLT 輸出**按鈕**XML 編輯器**工具列。

     XSLT 轉換結果的輸出會顯示在新的文件視窗和 [輸出] 視窗中使用的編輯器取決於檔案的副檔名您**輸出**文件屬性。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)