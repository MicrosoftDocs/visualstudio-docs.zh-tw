---
title: 選項、文字編輯器、XML、其他
description: 瞭解如何使用 XAML 區段中的 [其他] 頁面，變更 XML 編輯器的自動完成和架構設定。
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a02a2a133031661ecbf9c3719f3b1993f3b20b5b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040116"
---
# <a name="options-text-editor-xml-miscellaneous"></a>選項、文字編輯器、XML、其他

使用 [其他]選項來變更 XML 編輯器的自動完成和結構描述設定。 若要存取其他 XML 選項，請選擇 [**工具**  >  **選項**  >  **文字編輯器**  >  **XML**]，然後選擇 [**其他**]。

## <a name="auto-insert"></a>自動插入

**結尾標記**

撰寫 XML 項目時，文字編輯器會新增結尾標記。 如果選取元素開始標記，編輯器會插入相符的結尾標記，包括相符的命名空間前置詞。 依預設，這個核取方塊為已選取。

**屬性引號**

撰寫 XML 屬性時，編輯器會插入 `="` 和 `"` 字元，並將插入號 (**^**) 在引號內。 依預設，這個核取方塊為已選取。

**命名空間宣告**

編輯器在需要時會自動插入命名空間宣告。 依預設，這個核取方塊為已選取。

**其他標記 (註解、CDATA)**

註解、CDATA、DOCTYPE、處理指示，以及其他自動完成的標記。 依預設，這個核取方塊為已選取。

## <a name="network"></a>網路

**自動下載 DTD 和結構描述**

結構描述和文件類型定義 (DTD) 會從 HTTP 位置自動下載。 此功能使用 System.Net 並啟用 Autoproxy 伺服器偵測。 依預設，這個核取方塊為已選取。

## <a name="outlining"></a>大綱

**檔案開啟時進入大綱模式**

檔案開啟時啟動大綱功能。 依預設，這個核取方塊為已選取。

## <a name="caching"></a>Caching

**結構描述**

指定結構描述快取的位置。 [瀏覽] 按鈕會在新視窗中開啟目前的結構描述快取位置。 預設位置為 *%VsInstallDir%\xml\Schemas*。

## <a name="see-also"></a>另請參閱

- [XML 選項 - 格式化](options-text-editor-xml-formatting.md)
- [Visual Studio 中的 XML 工具](../../xml-tools/xml-tools-in-visual-studio.md)
