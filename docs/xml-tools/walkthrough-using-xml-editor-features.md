---
title: 逐步解說：使用 XML 編輯器功能
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8044c48ee2721a8461d9d7c2932707c3c01eeaf4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026746"
---
# <a name="walkthrough-use-xml-editor-features"></a>逐步解說：使用 XML 編輯器功能

此逐步教學中的步驟顯示如何建立新的 XML 文件。 逐步教學還會使用 XML 編輯器的部分功能，使其在 XML 撰寫上具有價值。

> [!NOTE]
> 開始本逐步解說之前, 儲存*hireDate.xsd*到本機電腦 （本主題中所包含以下） 的檔案。

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>建立新的 XML 檔案，並將它與 XML 結構描述產生關聯

1.  在上**檔案**功能表上，指向**新增**，然後按一下**檔案**。

2.  選取  **XML 檔案**中**範本**窗格，然後按一下 **開啟**。

     編輯器中會開啟新的檔案。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8">`。

3.  在 文件屬性 視窗中，按一下 瀏覽按鈕 (**...**) 上**結構描述**欄位。

     **XSD 結構描述**對話方塊隨即出現。

4.  按一下 [加入] 。

     **開啟 XSD 結構描述**對話方塊隨即出現。

5.  選取  *hireDate.xsd*檔案，然後按一下**開啟**。

6.  按一下 [確定 **Deploying Office Solutions**]。

     XML 結構描述現在已與 XML 文件相關聯。 XML 結構描述用於驗證文件。 它也由 IntelliSense 用於填入有效項目的成員清單。

## <a name="to-add-data"></a>加入資料

1.  在編輯器窗格中鍵入 `<`。

     成員清單會顯示可能的項目：

    -   **！-** 將註解。

    -   **!DOCTYPE**新增文件類型。

    -   **?** 若要加入處理指示。

    -   **員工**加入根項目。

2.  選取  **< ！-** 以新增註解節點，然後按**Enter**。

     編輯器會插入註解結束標記，並將游標置於開始與結束註解標記之間。

3.  在中輸入**測試 XML 檔案**。

4.  在新的一行中輸入`<`，然後選取**員工**從成員清單。

     編輯器會加入 XML 項目的開始部分，`<employee`。 此時您可以將屬性加入項目，或藉由鍵入 `>` 來關閉開始標記。

5.  鍵入 `>` 以關閉標記。

6.  編輯器會加入結束標記。 加入的結束標記會帶有波浪底線，表示驗證錯誤。 **工具提示**會顯示訊息：**項目 「 employee 」 的內容不完整。必須是 'ID'**。

7.  型別`<`，然後選取**識別碼**從成員清單。 然後鍵入 `>`。

     編輯器會加入 XML 項目 `<ID></ID>`，並將游標置於 ID 開始標記之後。

8.  型別**abc**。

     **Abc**文字帶有波浪底線。 **工具提示**會顯示訊息：**'ID' 項目有無效的值根據其資料型別**。

9. ID 項目上按一下滑鼠右鍵，然後選取**移至定義**。

     在編輯器開啟*hireDate.xsd*新的文件視窗中的檔案並將游標置於 ID 結構描述項目定義上。

10. 返回至 XML 檔案，並取代**abc**文字**123**。

     波浪底線及**工具提示**會清除 ID 項目值之下。 **工具提示**employee 結束標記現在會顯示訊息：**項目 「 employee 」 的內容不完整。必須是 '雇用日期'**。

11. 將游標置於 ID 結束標記之後，輸入`<`，選取**雇用日期**從 [成員] 清單中，然後再輸入`>`。

     編輯器會加入 XML 項目 `<hire-date></hire-date>`，並將游標置於 hire-date 開始標記之後。

12. 在中輸入**2003年-01-10**雇用日期值。

## <a name="to-format-the-xml-document"></a>格式化 XML 文件

- 選取 [**格式化文件**從 XML 編輯器] 工具列上的按鈕。

    會重新格式化 XML 文件。

## <a name="to-save-the-xml-document"></a>儲存 XML 文件

1.  從**檔案**功能表上，選取**另存新檔**。

     **另存新檔**對話方塊隨即出現。 預設檔名 *'XMLFile1'*。

2.  輸入檔案名稱和 XML 文件的位置，然後按一下**儲存**。

## <a name="hiredatexsd-file"></a>hireDate.xsd 檔案
 下列結構描述檔案由逐步教學使用。

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