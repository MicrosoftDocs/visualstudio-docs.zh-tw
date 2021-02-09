---
title: 逐步解說：使用 XML 編輯器功能
description: 若要瞭解如何建立新的 XML 檔，請遵循本逐步解說中的步驟來示範 XML 編輯器的功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45d0bb8b47162966974499fed20c826b52dcfaa4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875077"
---
# <a name="walkthrough-use-xml-editor-features"></a>逐步解說：使用 XML 編輯器功能

此逐步教學中的步驟顯示如何建立新的 XML 文件。 本逐步解說也會使用 XML 編輯器的一些功能，讓 XML 撰寫更加實用。

> [!NOTE]
> 開始本逐步解說之前，請先將本主題中所包含的「 *雇用」 .xsd* 檔 () 到本機電腦。

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>建立新的 XML 檔案，並將它與 XML 架構產生關聯

1. **在 [檔案**] 功能表上，指向 [**新增**]，**然後按一下 [** 檔案]。

2. 在 [**範本**] 窗格中選取 [ **XML** 檔案]，然後按一下 [**開啟**]。

     編輯器中會開啟新的檔案。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8">`。

3. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [流覽] 按鈕 (**...**) 。

     [ **XSD 架構** ] 對話方塊隨即顯示。

4. 按一下 **[新增]** 。

     [ **開啟 XSD 架構** ] 對話方塊隨即出現。

5. 選取 [ *雇用* 日期] .xsd 檔案，然後按一下 [ **開啟**]。

6. 按一下 [確定]  。

     XML 結構描述現在已與 XML 文件相關聯。 XML 結構描述用於驗證文件。 它也由 IntelliSense 用於填入有效項目的成員清單。

## <a name="to-add-data"></a>加入資料

1. 在編輯器窗格中鍵入 `<`。

     成員清單會顯示可能的項目：

    - **!--** 新增批註。

    - **!** 要新增檔案類型的 DOCTYPE。

    - **?** 加入處理指示。

    - 要加入根項目的 **員工**。

2. 選取 **&lt; !--** 加入 [批註] 節點，然後按 **enter** 鍵。

     編輯器會插入註解結束標記，並將游標置於開始與結束註解標記之間。

3. 輸入 **TEST XML file**。

4. 在新行上，輸入 `<` ，然後從成員清單中選取 **employee** 。

     編輯器會加入 XML 項目的開始部分，`<employee`。 此時您可以將屬性加入項目，或藉由鍵入 `>` 來關閉開始標記。

5. 鍵入 `>` 以關閉標記。

6. 編輯器會加入結束標記。 加入的結束標記會帶有波浪底線，表示驗證錯誤。 **工具提示** 會顯示訊息： **' employee ' 元素的內容不完整。應為 ' ID '**。

7. 輸入 `<` 並從成員清單中選取 [ **ID** ]。 然後鍵入 `>`。

     編輯器會加入 XML 項目 `<ID></ID>`，並將游標置於 ID 開始標記之後。

8. 輸入 **abc**。

     **Abc** 文字具有波浪底線。 **工具提示** 會顯示訊息： **' ID ' 元素根據其資料類型的值無效**。

9. 以滑鼠右鍵按一下 ID 元素，然後選取 [ **移至定義**]。

     編輯器會在新的文件視窗中開啟「 *雇用專案 .xsd* 」檔案，並將游標放在識別碼架構元素定義上。

10. 返回 XML 檔案，並將 **abc** 文字取代為 **123**。

     波浪底線和 **工具提示** 會在 ID 元素值下清除。 員工結束標記的 **工具提示** 現在會顯示訊息： **' employee ' 元素的內容不完整。應為 ' 雇用-date '**。

11. 將游標放在識別碼結束標記的後面，輸入 `<` ，從成員清單中選取 [ **雇用日期** ]，然後輸入 `>` 。

     編輯器會加入 XML 項目 `<hire-date></hire-date>`，並將游標置於 hire-date 開始標記之後。

12. 針對 [雇用日期] 值，輸入 **2003-01-10** 。

## <a name="to-format-the-xml-document"></a>格式化 XML 文件

- 選取 [XML 編輯器] 工具列上的 [**格式化檔**] 按鈕，或按下 **Ctrl** + **E**，**D**。

   ![Visual Studio 中的格式化 XML 檔按鈕](media/format-xml-document.png)

   會重新格式化 XML 文件。

## <a name="to-save-the-xml-document"></a>儲存 XML 文件

1. 從 [檔案] 功能表中選取 [另存新檔]。

     [ **另存** 新檔] 對話方塊隨即顯示。 預設檔案名為 *' XMLFile1 '*。

2. 輸入 XML 檔的檔案名和位置，然後按一下 [ **儲存**]。

## <a name="hiredatexsd-file"></a>雇傭 .xsd 檔案

本逐步解說會使用下列架構檔案：

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
