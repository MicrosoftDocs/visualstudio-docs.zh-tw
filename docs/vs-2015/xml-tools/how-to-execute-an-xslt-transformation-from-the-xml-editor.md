---
title: 如何：從 XML 編輯器執行 XSLT 轉換 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666540"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>HOW TO：從 XML 編輯器執行 XSLT 轉換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器可讓您將 XSLT 樣式表與 XML 文件相關聯、執行轉換，以及檢閱輸出。 XSLT 轉換的結果輸出會顯示在新文件視窗中。

 **Output**屬性會指定輸出的檔案名。 如果**Output**屬性是空白的，則臨時目錄中會產生檔案名。 副檔名以樣式表中的 `xsl:output` 項目為基礎，可以是 .xml、.txt 或 .htm。

 如果**Output**屬性指定副檔名為 .htm 或 .html 的檔案名，則會使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet EXPLORER 預覽 XSLT 輸出。 所有其他副檔名都使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio 所選擇的預設編輯器來開啟。 例如，如果副檔名為 .xml，則 Visual Studio 使用 XML 編輯器。

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>從 XML 文件執行 XSLT 轉換

1. 在 XML 編輯器中開啟 XML 文件。

2. 將 XSLT 樣式表與 XML 文件產生關聯。

    - 將 `xml-stylesheet` 處理指示加入 XML 文件。 例如，加入下列行 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 至文件初構。

         -或-

    - 使用 [**屬性**] 視窗加入 XSLT 樣式表單。 在 [檔**屬性] 視窗**中，按一下 [**樣式**表單] 欄位的 [**流覽]** 按鈕，選取 [XSLT 樣式表單]，然後按一下 [**開啟**]。

3. 按一下 [ **XML 編輯器**] 工具列上的 [ **ShowXSL 輸出**] 按鈕。

    > [!NOTE]
    > 如果沒有與 XML 文件相關聯的樣式表，則會出現一個對話方塊，提示您提供要使用的樣式表。
    >
    >  XSLT 轉換的結果輸出會顯示在新文件視窗中。

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>從 XSLT 樣式表執行 XSLT 轉換

1. 在 [XML 編輯器] 中開啟 XSLT 樣式表。

2. 在 [檔**屬性**] 視窗的 [**輸入**] 欄位中，指定 XML 檔。

    > [!NOTE]
    > XML 文件為用於轉換的輸入文件。 如果啟動 XSLT 轉換時未指定檔，則會出現 [開啟檔案] 對話方塊，您可以在該時間指定**檔**。

3. 按一下 [ **XML 編輯器**] 工具列上的 [ **ShowXSLT 輸出**] 按鈕。

     XSLT 轉換的結果輸出會顯示在新文件視窗中。

### <a name="to-provide-a-different-output-file-name"></a>提供不同的輸出檔案名稱

1. 在 [文檔**屬性**] 視窗的 [**輸出**] 欄位中指定檔案名。

2. 按一下 [ **XML 編輯器**] 工具列上的 [ **ShowXSLT 輸出**] 按鈕。

     XSLT 轉換的結果輸出會顯示在新的文件視窗中，而 [輸出] 視窗中使用的編輯器則取決於**輸出**文件屬性的副檔名。

## <a name="see-also"></a>請參閱
 [XML 編輯器](../xml-tools/xml-editor.md)
