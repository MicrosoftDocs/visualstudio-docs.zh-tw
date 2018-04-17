---
title: XML 結構描述和文件層級自訂中的資料 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8be23f82d03faa30cf8a6e180edb741c5f60814
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>文件層級自訂中的 XML 結構描述和資料
  **重要**本主題有關 Microsoft Word 中設定的資訊是呈現專用的效益和使用個人和組織使用者位於美國和其領域之外或人員使用，或開發在執行的程式，已由 Microsoft 授權年 1 月 2010、 Microsoft 實作的特定功能中移除時之前的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 不能讀取或由個人或組織在美國或其領域人員使用，或是在開發已由 Microsoft 授權，2010 年 1 月 10 日之後的 Microsoft Word 產品執行的程式中使用這項資訊有關 Microsoft Word;這些產品無法運作此日期之前的授權或購買與授權在美國以外的產品相同。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel 和 Microsoft Office Word 提供結構描述對應到您的文件的功能。 這項功能可以簡化匯入和匯出從文件的 XML 資料。  
  
 Visual Studio 會公開為控制項的程式設計模型中對應結構描述文件層級自訂中的項目。 For Excel，Visual Studio 會加入支援將控制項繫結至資料庫、 Web 服務和物件中的資料。 Word 和 Excel，Visual Studio 會加入執行窗格，可以使用結構描述對應的文件用來建立您的方案增強的使用者經驗的支援。 如需詳細資訊，請參閱 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
> [!NOTE]  
>  您無法在 Excel 方案中使用多部分的 XML 結構描述。  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>所建立的物件結構描述附加到 Excel 活頁簿時  
 結構描述附加至活頁簿時，Visual Studio 會自動建立數個物件，並將它們加入至您的專案。 這些物件不應該刪除使用 Visual Studio 工具，因為由 Excel。 若要刪除它們，移除工作表中的對應項目或卸離結構描述使用 Excel 的工具。  
  
 有兩個主要物件：  
  
-   XML 結構描述 （XSD 檔案）。 針對每個活頁簿中的結構描述，Visual Studio 會將結構描述加入至專案。 這會顯示為專案項目中的 XSD 延伸模組與**方案總管 中**。  
  
-   具型別 <xref:System.Data.DataSet> 類別。 這個類別會根據結構描述所建立。 這個資料集類別會顯示在**類別檢視**。  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>所建立的物件時結構描述元素會對應到 Excel 工作表  
 當您對應的結構描述項目，從**XML 來源**工作窗格加入工作表時，Visual Studio 會自動建立數個物件，然後將它們加入您的專案：  
  
-   控制項。 每個對應的物件在活頁簿， <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control （針對非重複的結構描述項目） 或<xref:Microsoft.Office.Tools.Excel.ListObject>control （針對重複結構描述項目） 的程式設計模型中建立。 <xref:Microsoft.Office.Tools.Excel.ListObject>可以刪除控制項，只要刪除活頁簿中的對應及對應的物件。 如需將控制項的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
-   BindingSource。 當您建立<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>非重複的結構描述項目對應至工作表，<xref:System.Windows.Forms.BindingSource>建立和<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項繫結至<xref:System.Windows.Forms.BindingSource>。 您必須將繫結<xref:System.Windows.Forms.BindingSource>符合結構描述對應至文件，例如具類型的執行個體的資料來源執行個體<xref:System.Data.DataSet>所建立的類別。 建立繫結設定<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>屬性，其會公開在**屬性**視窗。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource>未建立<xref:Microsoft.Office.Tools.Excel.ListObject>物件。 您必須以手動方式將繫結<xref:Microsoft.Office.Tools.Excel.ListObject>到資料來源，藉由設定<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的屬性**屬性**視窗。  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office 對應結構描述和 Visual Studio 資料來源視窗  
 這兩個對應的結構描述的功能 Office 和 Visual Studio**資料來源**視窗可協助您在進行報告或編輯 Excel 工作表上呈現資料。 在這兩種情況下您可以拖曳到 Excel 工作表的資料元素。 這兩種方法建立控制項進行資料繫結透過<xref:System.Windows.Forms.BindingSource>到資料來源，例如<xref:System.Data.DataSet>或 Web 服務。  
  
> [!NOTE]  
>  當您重複的結構描述項目對應至工作表時，Visual Studio 建立<xref:Microsoft.Office.Tools.Excel.ListObject>。 <xref:Microsoft.Office.Tools.Excel.ListObject>不會自動繫結至資料透過<xref:System.Windows.Forms.BindingSource>。 您必須以手動方式將繫結<xref:Microsoft.Office.Tools.Excel.ListObject>到資料來源，藉由設定<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的屬性**屬性**視窗。  
  
 下表顯示一些兩種方法之間的差異。  
  
|XML 結構描述|資料來源視窗|  
|----------------|-------------------------|  
|使用 Office 介面。|使用**資料來源**Visual Studio 中的視窗。|  
|可讓匯入和匯出資料，從 XML 檔案的內建 Office 功能。|您必須提供匯入和匯出功能，以程式設計的方式。|  
|您必須撰寫程式碼以填入資料產生的控制項。|從所加入的控制項**資料來源**視窗有來填入，以及必要的連接字串使用資料庫伺服器時自動產生的程式碼。|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>結構描述附加至 Word 文件時的行為  
 當您附加至 Word 文件的文件層級 Office 專案中所使用的結構描述，不會建立資料物件。 不過，當您加入文件對應的結構描述項目，會建立控制項。 控制項類型取決於您對應; 元素的類型重複項目會產生<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項和非重複的項目產生<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 如需詳細資訊，請參閱[XMLNodes 控制項](../vsto/xmlnodes-control.md)和[XMLNode 控制項](../vsto/xmlnode-control.md)。  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>包含 XML 結構描述的方案部署  
 您應該建立安裝程式，以部署使用對應至文件的 XML 結構描述的解決方案。 安裝程式應該在使用者電腦上的結構描述文件庫中註冊結構描述。 如果您沒有註冊的結構描述，解決方案仍可運作，因為 Word 會產生暫存的結構描述，根據在使用者開啟它時，是文件中的項目。 不過，使用者將無法執行或儲存用來建立專案的結構描述驗證。 如需安裝程式的詳細資訊，請參閱[部署應用程式、 服務和元件](/visualstudio/deployment/deploying-applications-services-and-components)。  
  
 您也可以將程式碼加入至專案，以檢查結構描述是否在程式庫並註冊。 如果不是，您可以警告使用者。  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 將結構描述對應至 Visual Studio 內的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [如何：在 Visual Studio 內將結構描述對應至工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  