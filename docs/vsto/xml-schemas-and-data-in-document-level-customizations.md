---
title: XML 結構描述和文件層級自訂中的資料
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb8bc9b9d3149112517d893cd3a704826b6d92d1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421685"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML 結構描述和文件層級自訂中的資料
  **重要**本主題有關 Microsoft Word 中設定的資訊是提供專門用於權益與使用個人和組織使用者位於外部皒玿璅其領域，或使用，或開發在執行的程式，第 2010 年 1 月 Microsoft 何時移除特定功能的實作之前由 Microsoft 所授權的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 有關 Microsoft Word 的這項資訊可能不會讀取或使用的個人或組織在美國或其區域使用，或開發在 2010 年 1 月 10 日之後由 Microsoft 所授權的 Microsoft Word 產品執行的程式;這些產品無法運作此日期之前的授權或購買，以在美國以外的使用授權的產品相同。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel 和 Microsoft Office Word 提供結構描述對應到您的文件的功能。 這項功能可以簡化匯入和匯出 XML 資料流入和流出文件。

 Visual Studio 會公開為控制項的程式設計模型中，對應結構描述文件層級自訂中的項目。 適用於 Excel、 Visual Studio 會加入支援的控制項繫結至資料庫、 Web 服務和物件中的資料。 Word 和 Excel，Visual Studio 會加入執行窗格，可以使用結構描述對應的文件用來建立您的解決方案的改進的使用者體驗的支援。 如需詳細資訊，請參閱 <<c0> [ 執行窗格概觀](../vsto/actions-pane-overview.md)。

> [!NOTE]
> 您無法在 Excel 方案中使用多部分的 XML 結構描述。

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>結構描述附加至 Excel 活頁簿時所建立的物件
 當您將結構描述附加至活頁簿時，Visual Studio 會自動建立數個物件，並將它們新增至您的專案。 這些物件不應刪除使用 Visual Studio 工具，因為它們由 Excel。 若要刪除它們，移除工作表中的對應項目或中斷連結結構描述使用 Excel 的工具。

 有兩個主要物件：

- XML 結構描述 （XSD 檔案）。 針對每個活頁簿中的結構描述，Visual Studio 會將結構描述加入至專案。 這會顯示為專案項目中副檔名為 XSD**方案總管 中**。

- 具型別 <xref:System.Data.DataSet> 類別。 這個類別會根據結構描述所建立。 這個資料集類別會顯示在**類別檢視**。

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>當結構描述元素會對應到 Excel 工作表時，所建立的物件
 當您將對應的結構描述項目，從**XML 來源**工作窗格加入工作表時，Visual Studio 自動建立數個物件，並將它們新增至您的專案：

- 控制項。 在活頁簿中的每個對應物件的<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>（適用於非重複的結構描述項目） 的控制項或<xref:Microsoft.Office.Tools.Excel.ListObject>（適用於重複結構描述項目） 的控制項的程式設計模型中建立。 <xref:Microsoft.Office.Tools.Excel.ListObject>可刪除控制項只是藉由從活頁簿中刪除對應和對應的物件。 如需控制項的詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

- BindingSource。 當您建立<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>非重複的結構描述元素對應至工作表中，<xref:System.Windows.Forms.BindingSource>會建立並<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項所繫結<xref:System.Windows.Forms.BindingSource>。 您必須將繫結<xref:System.Windows.Forms.BindingSource>執行個體的資料來源對應到文件，例如的具型別的執行個體的結構描述相符<xref:System.Data.DataSet>所建立的類別。 藉由設定建立繫結<xref:System.Windows.Forms.BindingSource.DataSource%2A>並<xref:System.Windows.Forms.BindingSource.DataMember%2A>屬性，其公開於**屬性**視窗。

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>不會建立<xref:Microsoft.Office.Tools.Excel.ListObject>物件。 您必須手動將繫結<xref:Microsoft.Office.Tools.Excel.ListObject>藉由設定資料來源<xref:System.Windows.Forms.BindingSource.DataSource%2A>並<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的屬性**屬性**視窗。

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office 對應結構描述和 Visual Studio 資料來源視窗
 這兩個對應的結構描述功能的 Office 和 Visual Studio **Zdroje dat**視窗可協助您在進行報告或編輯 Excel 工作表上呈現資料。 這兩種情況中，您可以拖曳資料項目到 Excel 工作表。 這兩種方法建立會透過繫結資料的控制項<xref:System.Windows.Forms.BindingSource>資料來源，例如<xref:System.Data.DataSet>或 web 服務。

> [!NOTE]
> 當您將重複的結構描述項目對應至工作表時，Visual Studio 建立<xref:Microsoft.Office.Tools.Excel.ListObject>。 <xref:Microsoft.Office.Tools.Excel.ListObject>不會自動繫結至資料透過<xref:System.Windows.Forms.BindingSource>。 您必須手動將繫結<xref:Microsoft.Office.Tools.Excel.ListObject>藉由設定資料來源<xref:System.Windows.Forms.BindingSource.DataSource%2A>並<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的屬性**屬性**視窗。

 下表顯示一些兩種方法之間的差異。

|XML 結構描述|資料來源視窗|
|----------------|-------------------------|
|使用 Office 介面。|會使用**Zdroje dat** Visual Studio 中的視窗。|
|啟用內建 Office 功能匯入和匯出資料，從 XML 檔案。|您必須提供匯入和匯出功能，以程式設計的方式。|
|您必須撰寫程式碼產生的控制項填入資料。|從新增的控制項**Zdroje dat**視窗有來填入，以及必要的連接字串，當您使用資料庫伺服器時自動產生的程式碼。|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>結構描述附加至 Word 文件時的行為
 當您附加至文件層級 Office 專案中使用的 Word 文件的結構描述，不會建立資料物件。 不過，當您將結構描述元素對應至文件時，會建立控制項。 控制項的型別取決於您將對應; 元素的類型重複項目產生<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項，以及非重複的項目產生<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 如需詳細資訊，請參閱 < [XMLNodes 控制項](../vsto/xmlnodes-control.md)並[XMLNode 控制項](../vsto/xmlnode-control.md)。

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>包含 XML 結構描述的解決方案的部署
 您應該建立安裝程式部署會使用對應至文件的 XML 結構描述的解決方案。 安裝程式應該在使用者電腦上的結構描述文件庫中註冊的結構描述。 如果您沒有註冊的結構描述，解決方案將仍會運作，因為 Word 產生暫存的結構描述，根據在使用者開啟它時是文件中的項目。 不過，使用者將無法執行或儲存用來建立專案的結構描述的驗證。 如需有關安裝程式的詳細資訊，請參閱 <<c0> [ 部署應用程式、 服務和元件](../deployment/deploying-applications-services-and-components.md)。

 您也可以加入程式碼專案，以檢查是否結構描述的程式庫，並註冊。 如果不是，您可以警告使用者。

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>另請參閱

- [如何：將結構描述對應至 Visual Studio 中的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [如何：將結構描述對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
