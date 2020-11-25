---
title: 執行 XSLT 轉換
description: 瞭解如何使用 XML 編輯器將 XSLT 樣式表單與 XML 檔產生關聯、執行 XSLT 轉換，以及查看輸出。
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1c7165f301c82dfaf5aa066a3e15bd7ab244089
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970241"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>如何：從 XML 編輯器執行 XSLT 轉換

XML 編輯器可讓您將 XSLT 樣式表單與 XML 檔產生關聯、執行轉換，並查看輸出。 XSLT 轉換的結果輸出會顯示在新文件視窗中。

**Output** 屬性指定輸出的檔案名。 如果 **輸出** 屬性是空白的，則會在臨時目錄中產生檔案名。 副檔名是根據 `xsl:output` 您的樣式表單中的元素，而且可以是。*xml*。*txt* 或。*htm*。

如果 **Output** 屬性指定包含的檔案名。*htm* 或。*html* 延伸模組：使用網頁瀏覽器預覽 XSLT 輸出。 所有其他副檔名都會使用 Visual Studio 所選擇的預設編輯器來開啟。 例如，如果副檔名為。*xml*，VISUAL STUDIO 使用 xml 編輯器。

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>從 XML 檔案執行 XSLT 轉換

1. 在 XML 編輯器中開啟 XML 檔。

2. 將 XSLT 樣式表與 XML 文件產生關聯。

    - 將 `xml-stylesheet` 處理指示加入 XML 文件。 例如，將下列這一行新增至檔初構： `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -或-

    - 使用 [ **屬性** ] 視窗加入 XSLT 樣式表單。 在編輯器中開啟 XML 檔案時，以滑鼠右鍵按一下編輯器中的任何位置，然後選擇 [ **屬性**]。 在 [ **屬性** ] 視窗的 [ **樣式** 表單] 欄位中按一下，然後選擇 [流覽] 按鈕 ( ... ) 。選取 [XSLT 樣式表單]，然後選擇 [ **開啟**]。

3. 在功能表列上，選擇 [ **XML**  >  **啟動 XSLT 而不進行調試**]。 或者，按下 **Ctrl** + **Alt** + **F5**。

   XSLT 轉換的輸出會顯示在新的文件視窗中。

   > [!NOTE]
   > 如果沒有與 XML 文件相關聯的樣式表，則會出現一個對話方塊，提示您提供要使用的樣式表。

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>從 XSLT 樣式表單執行 XSLT 轉換

1. 在 XML 編輯器中開啟 XSLT 樣式表單。

2. 在 [檔 **屬性**] 視窗的 [**輸入**] 欄位中指定 XML 檔。

   > [!NOTE]
   > XML 文件為用於轉換的輸入文件。 如果在啟動 XSLT 轉換時未指定檔，[開啟檔案] 對話方塊隨即出現，而且您可以指定該時間的 **檔** 。

3. 在功能表列上，選擇 [ **XML**  >  **啟動 XSLT 而不進行調試**]。 或者，按下 **Ctrl** + **Alt** + **F5**。

   XSLT 轉換的輸出會顯示在新的文件視窗中。

## <a name="specify-an-output-file-name"></a>指定輸出檔名稱

您可以指定 XML 和 XSL 檔案的輸出檔名稱。 開啟 [ **屬性** ] 視窗，並在 [ **輸出** ] 欄位中指定檔案名。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
