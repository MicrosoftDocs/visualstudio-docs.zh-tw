---
title: 逐步解說：內容控制項繫結至自訂 XML 組件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52366cc268335df98da53701e5cde283c67a022d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438710"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>逐步解說：內容控制項繫結至自訂 XML 組件
  本逐步解說示範如何將 Word 之文件層級自訂中的內容控制項繫結至文件中所儲存的 XML 資料。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word 可讓您儲存 XML 資料，名為*自訂 XML 組件*，文件中。 將內容控制項繫結至自訂 XML 組件中的項目，即可控制這項資料的顯示。 本逐步解說中的範例文件會顯示自訂 XML 組件中所儲存的員工資訊。 開啟文件時，內容控制項會顯示 XML 項目的值。 您對內容控制項中文字進行的任何變更都會儲存在自訂 XML 組件中。

 這個逐步解說將說明下列工作：

- 在設計階段，將內容控制項新增至文件層級專案中的 Word 文件。

- 建立 XML 資料檔，以及定義項目以繫結至內容控制項的 XML 結構描述。

- 在設計階段，將 XML 結構描述附加至文件。

- 加入在執行階段文件中的自訂 XML 組件中的 XML 檔案的內容。

- 將內容控制項繫結至自訂 XML 組件中的項目。

- 將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至 XML 結構描述中所定義的一組值。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-new-word-document-project"></a>建立新的 Word 文件專案
 建立將在逐步解說中使用的 Word 文件。

### <a name="to-create-a-new-word-document-project"></a>建立新的 Word 文件專案

1. 建立 Word 文件專案名稱**EmployeeControls**。 建立方案的新文件。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在設計工具中開啟新的 Word 文件，並將**EmployeeControls**專案加入**方案總管 中**。

## <a name="add-content-controls-to-the-document"></a>將內容控制項加入文件
 建立包含三種不同類型之內容控制項的資料表，使用者可以使用這些內容控制項來檢視或編輯員工相關資訊。

### <a name="to-add-content-controls-to-the-document"></a>將內容控制項新增至文件

1. 在 Word 文件中裝載[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]設計工具中的，在功能區中，選擇**插入** 索引標籤。

2. 在 **資料表**群組中，選擇**資料表**，並插入具有 2 個資料行和 3 個資料列的資料表。

3. 在第一個資料行中輸入文字，讓它類似下面資料行：

   ||
   |-|
   |**員工名稱**|
   |**雇用日期**|
   |**標題**|

4. 在資料表的第二個資料行，選擇 第一個資料列 (旁**員工姓名**)。

5. 在功能區中，選擇**開發人員** 索引標籤。

   > [!NOTE]
   > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。

6. 在 [**控制項**群組中，選擇**文字**] 按鈕![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl")新增<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>第一個資料格中。

7. 在資料表的第二個資料行，選擇 第二個資料列 (旁**雇用日期**)。

8. 在 [**控制項**群組中，選擇**日期選擇器**] 按鈕![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl")新增<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>到第二個儲存格。

9. 在資料表的第二個資料行，選擇 第三個資料列 (旁**Title**)。

10. 在 [**控制項**群組中，選擇**下拉式清單**] 按鈕![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl")新增<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>最後一個儲存格。

    這是此專案的整個使用者介面。 如果您立即執行專案，則可以在第一個資料列中輸入文字，並在第二個資料列選取日期。 下一個步驟是將您想要顯示的資料附加至 XML 檔案中的文件。

## <a name="create-the-xml-data-file"></a>建立 XML 資料檔
 通常，您會從外部來源 (例如檔案或資料庫) 取得要儲存在自訂 XML 組件中的 XML 資料。 在本逐步解說中，您會建立包含員工資料的 XML 檔案，而員工資料會標上將繫結至文件中內容控制項的項目。 若要將資料設為可在執行階段使用，請內嵌 XML 檔案做為自訂組件中的資源。

#### <a name="to-create-the-data-file"></a>建立資料檔

1. 在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。

     [新增項目] 對話方塊隨即出現。

2. 在 **範本**窗格中，選取**XML 檔案**。

3. 將檔案命名**employees.xml**，然後選擇**新增** 按鈕。

     **Employees.xml**隨即在程式碼編輯器中開啟。

4. 內容取代**employees.xml**包含下列文字的檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. 在 **方案總管**，選擇**employees.xml**檔案。

6. 在 **屬性**視窗中，選取**建置動作**屬性，然後將值變更為**內嵌資源**。

     此步驟會在您建置專案時，將 XML 檔案內嵌為組件中的資源。 這可讓您存取在執行階段的 XML 檔案的內容。

## <a name="create-an-xml-schema"></a>建立 XML 結構描述
 如果您想要將內容控制項繫結至自訂 XML 組件中的單一項目，則不需要使用 XML 結構描述。 不過，若要將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至一組值，您必須建立 XML 結構描述，以驗證您稍早建立的 XML 資料檔。 XML 結構描述定義 `title` 項目的可能值。 稍後，您將在本逐步解說中將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至此項目。

#### <a name="to-create-an-xml-schema"></a>建立 XML 結構描述

1. 在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。

     [新增項目] 對話方塊隨即出現。

2. 在 **範本**窗格中，選取**XML 結構描述**。

3. 將結構描述**employees.xsd** ，然後選擇**新增** 按鈕。

     結構描述設計工具隨即開啟。

4. 在 **方案總管 中**，開啟捷徑功能表**employees.xsd**，然後選擇 **檢視程式碼**。

5. 內容取代**employees.xsd**具有下列結構描述檔案。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. 上**檔案**功能表上，按一下**全部儲存**以儲存您的變更**employees.xml**而**employees.xsd**檔案。

## <a name="attach-the-xml-schema-to-the-document"></a>將 XML 結構描述附加至文件
 您必須將 XML 結構描述附加至文件，以將 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 繫結至 `title` 項目的有效值。

### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>若要將 XML 結構描述附加至文件 ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])

1. 啟用**EmployeeControls.docx**設計工具中。

2. 在功能區中，選擇**開發人員**索引標籤，然後選擇**增益集** 按鈕。

3. 在 **範本與增益集**對話方塊方塊中，選擇**XML 結構描述**索引標籤，然後選擇 **新增結構描述** 按鈕。

4. 瀏覽至**employees.xsd**結構描述您稍早建立，這位於您的專案目錄，然後選擇**開啟** 按鈕。

5. 選擇**確定**按鈕**結構描述設定** 對話方塊。

6. 選擇**確定**按鈕以關閉**範本與增益集** 對話方塊。

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>將 XML 結構描述附加至文件 (Word 2010)

1. 啟用**EmployeeControls.docx**設計工具中。

2. 在功能區中，選擇**開發人員** 索引標籤。

3. 在 [ **XML**群組中，選擇**結構描述**] 按鈕。

4. 在 **範本與增益集**對話方塊方塊中，選擇**XML 結構描述**索引標籤，然後選擇 **新增結構描述** 按鈕。

5. 瀏覽至**employees.xsd**結構描述，您在稍早所建立位於您的專案目錄，然後選擇**開啟** 按鈕。

6. 選擇**確定**按鈕**結構描述設定** 對話方塊。

7. 選擇**確定**按鈕以關閉**範本與增益集** 對話方塊。

     **XML 結構**工作窗格隨即開啟。

8. 關閉**XML 結構**工作窗格。

## <a name="add-a-custom-xml-part-to-the-document"></a>將自訂 XML 組件新增至文件
 您必須先將 XML 檔案的內容新增至文件中的新自訂 XML 組件，才能將內容控制項繫結至 XML 檔案中的項目。

### <a name="to-add-a-custom-xml-part-to-the-document"></a>將自訂 XML 組件新增至文件

1. 在**方案總管**，開啟捷徑功能表**ThisDocument.cs**或**ThisDocument.vb**，然後選擇**檢視程式碼**。

2. 將下列宣告新增至 `ThisDocument` 類別： 此程式碼會宣告數個物件，以用來將自訂 XML 組件新增至文件。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. 將下列方法加入 `ThisDocument` 類別。 這個方法會取得內嵌為組件中資源的 XML 資料檔內容，並以 XML 字串形式傳回內容。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. 將下列方法加入 `ThisDocument` 類別。 `AddCustomXmlPart` 方法會建立新的自訂 XML 組件，其中包含傳遞至此方法的 XML 字串。

     若要確保自訂 XML 組件只建立一次，只有在文件中還沒有具有相符 GUID 的自訂 XML 組件時，此方法才會建立自訂 XML 組件。 第一次呼叫此方法時，它會將 <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> 屬性的值儲存至 `employeeXMLPartID` 字串。 `employeeXMLPartID` 字串的值會保存在文件中，因為它是使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性所宣告。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>將內容控制項繫結至自訂 XML 組件中的項目
 將每個內容控制項繫結至自訂 XML 組件中的項目利用**XMLMapping**各個內容控制項的屬性。

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>將內容控制項繫結至自訂 XML 組件中的項目

1. 將下列方法加入 `ThisDocument` 類別。 此方法會將每個內容控制項繫結至自訂 XML 組件中的項目，並設定 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 的日期顯示格式。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>開啟文件時執行您的程式碼
 建立自訂 XML 組件，並在開啟文件時，將自訂控制項繫結至資料。

### <a name="to-run-your-code-when-the-document-is-opened"></a>在開啟文件時執行程式碼

1. 將下面程式碼加新增至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法。 此程式碼會取得 XML 字串，從**employees.xml**檔案，將 XML 字串新增至新的自訂 XML 組件，並將內容控制項繫結至自訂 XML 組件中的項目。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>測試專案
 開啟文件時，內容控制項會顯示自訂 XML 組件中項目的資料。 您可以按一下<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>以選取其中一個的三個有效值`title`元素，其定義於**employees.xsd**檔案。 如果您編輯任何內容控制項中的資料，則新的值會儲存在文件的自訂 XML 組件中。

### <a name="to-test-the-content-controls"></a>測試內容控制項

1. 按 **F5** 執行專案。

2. 請確認文件中的資料表類似於下表。 第二個資料行中的每個字串都會取自文件之自訂 XML 組件中的項目。

    |||
    |-|-|
    |**員工名稱**|**Karina Leal**|
    |**雇用日期**|**1999 年 4 月 1日日**|
    |**標題**|**Manager**|

3. 選擇右邊的儲存格**員工姓名**資料格，然後輸入不同的名稱。

4. 選擇右邊的儲存格**雇用日期**資料格，然後在 日期選擇器中選取不同的日期。

5. 選擇右邊的儲存格**Title**資料格，然後從下拉式清單中選取新的項目。

6. 儲存並關閉文件。

7. 在 [檔案總管] 中，開啟*\bin\Debug*您的專案位置下的資料夾。

8. 開啟捷徑功能表**EmployeeControls.docx** ，然後選擇**重新命名**。

9. 將檔案命名**EmployeeControls.docx.zip**。

     **EmployeeControls.docx** Open XML 格式儲存文件。 重新命名此文件，藉以 *.zip*副檔名，您可以檢查文件的內容。 如需有關 Open XML 的詳細資訊，請參閱技術文件[簡介 Office (2007) Open XML 檔案格式](/previous-versions/office/developer/office-2007/aa338205(v=office.12))。

10. 開啟**EmployeeControls.docx.zip**檔案。

11. 開啟**customXml**資料夾。

12. 開啟捷徑功能表**item2.xml** ，然後選擇**開啟**。

     此檔案包含您已新增至文件的自訂 XML 組件。

13. 請確認 `name`、`hireDate` 和 `title` 項目包含您在文件中的內容控制項中輸入的新值。

14. 關閉**item2.xml**檔案。

## <a name="next-steps"></a>後續步驟
 您可以透過下列主題，進一步了解如何使用內容控制項：

- 使用所有可用的內容控制項來建立範本。 如需詳細資訊，請參閱[逐步解說：使用內容控制項建立範本](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)。

- 在關閉文件時，修改自訂 XML 組件中的資料。 下次使用者開啟文件時，繫結至 XML 項目的內容控制項會顯示新的資料。

- 使用內容控制項保護文件的組件。 如需詳細資訊，請參閱[如何：使用內容控制項保護文件的部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)。

## <a name="see-also"></a>另請參閱
- [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [內容控制項](../vsto/content-controls.md)
- [如何：將內容控制項加入 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)
- [如何：使用內容控制項保護文件的組件](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
