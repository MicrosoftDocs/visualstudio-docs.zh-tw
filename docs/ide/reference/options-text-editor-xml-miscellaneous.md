---
title: 選項、文字編輯器、XML、其他
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58de904e1697a820a2f4bc6f88fbff5237cabc30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666581"
---
# <a name="options-text-editor-xml-miscellaneous"></a>選項、文字編輯器、XML、其他

使用 [其他]選項來變更 XML 編輯器的自動完成和結構描述設定。 如果要存取其他 XML 選項，請選擇 [工具] > [選項] > [文字編輯器] > [XML]，然後選擇 [其他]。

## <a name="auto-insert"></a>自動插入

**結尾標記**

撰寫 XML 項目時，文字編輯器會新增結尾標記。 如果選取了項目起始標記，則編輯器會插入相符的結尾標記，包括相符的命名空間前置詞。 預設情況下會選取此核取方塊。

**屬性引號**

撰寫 XML 屬性時，編輯器會插入 `="` 和 `"` 字元，並將插入號 ( **^** ) 置於引號內。 預設情況下會選取此核取方塊。

**命名空間宣告**

編輯器會自動在需要的位置插入命名空間宣告。 預設情況下會選取此核取方塊。

**其他標記 (註解、CDATA)**

自動完成註解、CDATA、DOCTYPE、處理指示及其他標記。 預設情況下會選取此核取方塊。

## <a name="network"></a>網路

**自動下載 DTD 及結構描述**

自動從 HTTP 位置下載結構描述及文件類型定義 (DTD)。 此功能會使用已啟用自動 Proxy 伺服器偵測的 System.Net。 預設情況下會選取此核取方塊。

## <a name="outlining"></a>大綱

**檔案開啟時進入大綱模式**

會在檔案開始時開啟大綱功能。 預設情況下會選取此核取方塊。

## <a name="caching"></a>快取

**結構描述**

指定結構描述快取的位置。 [瀏覽] 按鈕會在新視窗中開啟目前的結構描述快取位置。 預設位置為 *%VsInstallDir%\xml\Schemas*。

## <a name="see-also"></a>請參閱

- [XML 選項 - 格式化](options-text-editor-xml-formatting.md)
- [Visual Studio 中的 XML 工具](../../xml-tools/xml-tools-in-visual-studio.md)