---
title: XML 編輯器 IntelliSense 功能
description: 您可以在 Visual Studio 瞭解 XML 編輯器的 IntelliSense 功能，以及如何搭配 XML 架構定義語言 (XSD) 和 XSLT 檔使用這些功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 330dbdfb6d6db8d33a2b8ea3caa7e1a840d84dd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874895"
---
# <a name="xml-editor-intellisense-features"></a>XML 編輯器 IntelliSense 功能

XML 編輯器提供完整的 Intellisense 功能，其相當於 Visual Studio 中提供的其他語言編輯器。 本節說明如何使用 IntelliSense (XSLT) 搭配 XML 結構定義語言 (XSD) 與 XSLT 文件。

## <a name="intellisense-in-an-xsd-document"></a>XSD 檔中的 IntelliSense

在架構與您的檔相關聯之後，您可以在輸入 `"<"` 或按一下 XML 編輯器工具列上的 [ **顯示物件成員清單** ] 按鈕時，取得預期專案的下拉式清單。

![顯示物件成員清單按鈕](media/display-object-member-list-xml.png)

如需有關如何將架構與 XML 檔產生關聯的詳細資訊，請參閱 [xml 檔驗證](../xml-tools/xml-document-validation.md)。

從開始標記內鍵入 SPACE 時，您也會取得一個下拉式清單，顯示可加入到目前項目的全部屬性。

針對屬性值鍵入 `"="`，或鍵入值的開頭引號時，也會取得該屬性的可能值清單。 只有透過 `xsd:enumeration` Facet 提供列舉值，或者屬性是 `Boolean` 型別時，才會提供值。 還會為 `xml:lang` 或衍生自 `simpleType` 的任何 `xsd:language`，提供已知語言代碼的 IntelliSense 清單。 會為命名空間宣告提供已知 `targetNamespace` 值的 IntelliSense 清單。

如果項目是 `">"`，則當您鍵入 `simpleType` 以關閉開始標記時，還會提供可能值的 IntelliSense 清單。 項目的行為與前一段中說明的屬性行為相類似。

根據在相關結構描述中找到的 `xsd:annotation` 及 `xsd:documentation` 資訊，這些 IntelliSense 清單上還會出現工具提示。

## <a name="intellisense-in-an-xslt-document"></a>XSLT 檔中的 IntelliSense

在您將具名範本或屬性加入至 XSLT 文件後，即可使用 IntelliSense 插入下列內容：

- 屬性集名稱。

- 範本模式。

- 範本名稱。

- 指定模式的參數名稱。‏

- 指定具名範本的參數名稱。‏

如需詳細資訊，請參閱 [逐步解說：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) 主題。

## <a name="auto-completion"></a>自動完成

XML 編輯器還可藉由填入必要的 XML 語法，使編輯 XML 變得更容易。 例如，如果您鍵入下列開始標記：

`<book>`

XML 編輯器會填入結束標記，並將游標置於開啟標記後面。 以下是此 (「&#124;」附注游標位置) 的範例：

`<book>`&#124;`</book>`

因為屬性值必須永遠帶有引號，所以 XML 編輯器會填入引號。 例如，如果您鍵入下列內容：

`<book title=`

XML 編輯器會加入引號，並將游標置於引號之間：

`<book title="`&#124;`"`

同樣地，XML 編輯器還會自動插入下列 XML 語法：

- 結束處理指示：`?>`

- 結束 CDATA 區塊：`]]>`

- 結束註解：`-->`

- 結束 DTD 宣告：`>`

如果您從 IntelliSense 清單中選取命名空間限定的元素或屬性，且該專案或屬性的命名空間尚未在範圍內，則 XML 編輯器也可以插入命名空間宣告。

例如，如果您從 IntelliSense 清單中選取 `e:Book` 項目，該清單中的前置詞繫結至尚未在文件中宣告的 `http://books` 命名空間，則 XML 編輯器會插入必要的命名空間宣告。 下列是產生的 XML 文字：

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>括號對稱

XML 編輯器提供括號反白顯示，以將您剛剛關閉之項目的立即回應提供給您。 您也可以使用鍵盤快速鍵 (**Ctrl** + **]**) 從一個大括弧跳至相符的大括弧。

XML 編輯器會針對下列項目執行此操作：

- 對稱的開始與結束標記。

- 任何一對 "\<" or ">" 角括號。

- 註解的開始與結束。

- 處理指示的開始與結束。

- CDATA 區塊的開始與結束。

- DTD 宣告的開始與結束。

- 屬性上的開頭及結束引號。

## <a name="modify-the-intellisense-options"></a>修改 IntelliSense 選項

依預設會啟用 IntelliSense 及自動完成功能。 不過，您可以藉由修改 **工具**  >  **選項** 設定來變更。

[**其他**] 頁面的 [**自動插入**] 區段會控制下列行為：

|名稱|描述|
|-|-----------------|
|結尾標記|插入新項目的關閉標記。|
|屬性引號|輸入新屬性名稱時，請插入屬性值引號。|
|其他標記|完成註解、CDATA、DOCTYPE、處理指示及其他標記宣告。|

### <a name="to-change-the-auto-completion-behavior"></a>變更自動完成行為

1. 選取 [工具] 功能表上的 [選項]。

2. 展開 [ **文字編輯器**]，展開 [ **XML**]，然後選取 [ **其他**]。

3. 對 [ **自動插入** ] 區段進行任何變更，然後按一下 **[確定]**。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
- [使用 IntelliSense](../ide/using-intellisense.md)
- [逐步解說：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)
