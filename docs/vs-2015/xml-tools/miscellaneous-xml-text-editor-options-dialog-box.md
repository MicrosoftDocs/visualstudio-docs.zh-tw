---
title: 選項對話方塊、文字編輯器、其他、XML |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656241"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>其他、XML、文字編輯器、選項對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此對話方塊可讓您變更 XML 編輯器的自動完成及結構描述設定。 您可以從 [**工具**] 功能表存取 [**選項**] 對話方塊。

> [!NOTE]
> 當您選取 [**文字編輯器**] 資料夾、[ **XML** ] 資料夾，以及 [**選項**] 對話方塊中的 [**其他**] 選項時，即可使用這些設定。

## <a name="auto-insert"></a>自動插入
 **關閉標記**如果已核取 [自動完成] 設定，當您輸入右角括弧（>）來關閉開始標記（如果標記尚未關閉）時，編輯器會自動新增結束標記。 這是預設行為。

 空白項目的完成不會依賴自動完成設定。 您可以隨時輸入反斜線 (/) 以自動完成空白項目。

 **屬性引號**撰寫 XML 屬性時，編輯器會插入 `=" "` 的字元，並將插入號（^）置於雙引號內。

 預設會選取。

 **命名空間**宣告編輯器會在需要的地方自動插入命名空間宣告。

 預設會選取。

 **其他標記（批註、CDATA）** 批註、CDATA、DOCTYPE、處理指示及其他標記都會自動完成。

 預設會選取。

## <a name="network"></a>網路
 **自動下載 dtd 和架構**架構和檔案類型定義（Dtd）會從 HTTP 位置自動下載。 此功能會使用已啟用自動 Proxy 伺服器偵測的 System.Net。

 預設會選取。

## <a name="outlining"></a>大綱
 **當檔案開啟時進入大綱模式**開啟檔案時開啟大綱功能。

 預設會選取。

## <a name="caching"></a>快取
 **架構**指定架構快取的位置。 瀏覽按鈕（ **...** ）會在目前的架構快取位置開啟 [**瀏覽目錄**] 對話方塊。 您可以選取不同的目錄，也可以在對話方塊中選取資料夾、按一下滑鼠右鍵，然後選擇 [**開啟**] 以查看目錄中的內容。

## <a name="see-also"></a>請參閱
 [Xml 文件屬性、屬性視窗](../xml-tools/xml-document-properties-properties-window.md) [xml 編輯器元件](../xml-tools/xml-editor-components.md)
