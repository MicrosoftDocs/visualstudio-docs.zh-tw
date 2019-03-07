---
title: 執行 XSLT 轉換
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526369"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>HOW TO：從 XML 編輯器執行 XSLT 轉換

XML 編輯器可讓您將 XSLT 樣式表與 XML 文件產生關聯、 執行轉換，以及檢視輸出。 XSLT 轉換的結果輸出會顯示在新文件視窗中。

**輸出**屬性指定輸出的檔案名稱。 如果**輸出**屬性為空白，就會產生檔名，暫存目錄中。 副檔名根據`xsl:output`項目，以您的樣式表，而且可以是。*xml*，。*txt*或。*htm*。

如果**輸出**屬性指定的檔名。*htm*或。*html*延伸模組，XSLT 輸出是預覽使用網頁瀏覽器。 所有其他檔案延伸模組會使用 Visual Studio 所選擇的預設編輯器來開啟。 例如，如果檔案的副檔名。*xml*，Visual Studio 會使用 XML 編輯器。

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>從 XML 檔案中執行 XSLT 轉換

1. 在 XML 編輯器中開啟 XML 文件。

2. 將 XSLT 樣式表與 XML 文件產生關聯。

    - 將 `xml-stylesheet` 處理指示加入 XML 文件。 比方說，將下面這一行新增至文件初構中： `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -或-

    - 加入 XSLT 樣式表 using**屬性**視窗。 在編輯器中開啟的 XML 檔案，以滑鼠右鍵按一下編輯器中的任何位置，然後選擇**屬性**。 在 **屬性** 視窗中，按一下**樣式表**欄位，然後選擇 瀏覽按鈕 （...）。選取 XSLT 樣式表，然後選擇**開啟**。

3. 在功能表列上選擇  **XML** > **啟動 XSLT 但不偵錯**。 或者，您也可以按下**Ctrl**+**Alt**+**F5**。

   XSLT 轉換的輸出會顯示在新的文件視窗。

   > [!NOTE]
   > 如果沒有與 XML 文件相關聯的樣式表，則會出現一個對話方塊，提示您提供要使用的樣式表。

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>從 XSLT 樣式表執行 XSLT 轉換

1. 在 XML 編輯器中開啟 XSLT 樣式表。

2. 指定在 XML 文件**輸入**欄位的文件**屬性**視窗。

   > [!NOTE]
   > XML 文件為用於轉換的輸入文件。 如果啟動 XSLT 轉換時，未指定文件，則**開啟舊檔** 對話方塊隨即出現，而且您可以指定文件，在該時間。

3. 在功能表列上選擇  **XML** > **啟動 XSLT 但不偵錯**。 或者，您也可以按下**Ctrl**+**Alt**+**F5**。

   XSLT 轉換的輸出會顯示在新的文件視窗。

## <a name="specify-an-output-file-name"></a>指定輸出檔名稱

您可以指定 XML 和 XSL 檔案的輸出檔案名稱。 開啟**屬性** 視窗，並指定中的檔案名稱**輸出**欄位。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)