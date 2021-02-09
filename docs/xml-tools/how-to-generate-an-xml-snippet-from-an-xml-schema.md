---
title: HOW TO：從 XML 結構描述產生 XML 片段
description: 瞭解如何使用 XML 編輯器，從 XML 架構定義語言 (XSD) 架構產生 XML 片段。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e73834888009ff547bb4252aaedafb713ce9c2fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897468"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>如何：從 XML 架構產生 XML 片段

XML 編輯器可以從 XML 架構定義語言 (XSD) 架構產生 XML 片段。 例如，當您在撰寫 XML 檔案時，如果在專案名稱旁邊放置，您可以按 **tab** 鍵，以從該專案的架構資訊產生的 xml 資料填入專案。

此功能僅可用於項目。 下列規則也適用：

- 項目必須具有相關聯的結構描述型別，即根據某些相關聯的結構描述，此項目必須是有效的。 結構描述型別不能是抽象的，且型別必須包含必要的屬性及/或必要的項目子系。

- 編輯器中目前的項目必須是空的，沒有屬性。 例如，下列內容全部有效

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- 游標必須緊接在項目名稱的右邊。

產生的片段包含所有必要的屬性及項目。 如果 `minOccurs` 大於一，則片段中會包括該項目必要執行個體的最小數目 (上限為 100 個執行個體)。 在結構描述結果中找到的任何固定值均會在片段中產生固定值。 系統會忽略 `xsd:any` 和 `xsd:anyAttribute` 項目，因此不會額外產生任何片段建構。

會產生預設值，並記錄為可編輯的值。 如果結構描述指定預設值，則會使用此預設值。 但是，如果結構描述預設值是空字串，則編輯器會以下列方式產生預設值：

- 如果結構描述型別包含任何列舉型別 Facet (直接或間接透過聯集型別的任何成員)，則會使用在結構描述物件模型中找到的第一個列舉值做為預設值。

- 如果結構描述型別是原子型別，則編輯器會取得原子型別並插入原子型別名稱。 若為衍生的簡單型別，它會使用基底簡單型別。 若為清單型別，則原子型別為 `itemType`。 若為聯集型別，則原子型別為第一個 `memberType` 的原子型別。

## <a name="example"></a>範例

本節中的步驟示範如何使用 XML 編輯器的架構產生 XML 片段功能。

> [!NOTE]
> 先將結構描述檔案儲存到本機電腦上，再啟動這些程序。

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>建立新的 XML 檔案，並將它與 XML 架構產生關聯

1. **在 [檔案**] 功能表上，指向 [**新增**]，**然後按一下 [** 檔案]。

2. 在 [**範本**] 窗格中選取 [ **XML** 檔案]，然後按一下 [**開啟**]。

     編輯器中會開啟新的檔案。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8">`。

3. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [流覽] 按鈕 (**...**) 。

     [ **XSD 架構** ] 對話方塊隨即顯示。

4. 按一下 **[新增]** 。

     [ **開啟 XSD 架構** ] 對話方塊隨即出現。

5. 選取架構檔案，然後按一下 [ **開啟**]。

6. 按一下 [確定]  。

     XML 架構現在與 XML 檔相關聯。

### <a name="to-generate-an-xml-snippet"></a>產生 XML 片段

1. 在編輯器窗格中鍵入 `<`。

2. 成員清單會顯示可能的項目：

     **!--** 新增批註。

     **!** 要新增檔案類型的 DOCTYPE。

     **?** 加入處理指示。

     加入根項目的 **連絡人**。

3. 從成員清單中選取 [ **Contact** ]，然後按 **enter**。

     編輯器會加入開始標記 `<Contact`，並將游標置於項目名稱之後。

4. 按 **tab** 鍵，根據專案的架構資訊產生元素的 XML 資料 `Contact` 。

## <a name="input"></a>輸入

下列結構描述檔案由逐步教學使用。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>輸出

下列是根據與 `Contact` 項目相關聯的結構描述資訊產生的 XML 資料。 標記為的專案會 `bold` 指定 XML 片段中的可編輯欄位。

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>另請參閱

- [XML 片段](../xml-tools/xml-snippets.md)
- [如何：使用 XML 程式碼片段](../xml-tools/how-to-use-xml-snippets.md)
