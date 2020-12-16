---
title: 檔層級自訂中的 XML 架構和資料
description: Microsoft Excel 和 Word 提供將架構對應至檔的功能，並可簡化在檔中匯入和匯出 XML 資料的功能。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 57fad7982f762c4837399e12552cd109c9a9086c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527857"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>檔層級自訂中的 XML 架構和資料
  **重要** 本主題中有關 Microsoft Word 的資訊，只會提供給位於美國以外的個人和組織，或使用或正在開發的 microsoft word 產品（在2010年1月之前由 Microsoft 授權的 microsoft Word 產品），而 Microsoft 已從 Microsoft Word 移除與自訂 XML 相關的特定功能。 這項有關 Microsoft Word 的資訊，可能無法由美國的個人或組織、在2010年1月10日之後由 Microsoft 授權的 Microsoft Word 產品所使用的 microsoft word 產品或開發人員所使用;這些產品的行為不像在該日期之前授權的產品，或購買並授權在美國以外地區使用。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel 和 Microsoft Office Word 提供將架構對應至檔的功能。 這項功能可以簡化匯入和匯出檔中的 XML 資料。

 Visual Studio 會將檔層級自訂中的對應架構元素公開為程式設計模型中的控制項。 針對 Excel，Visual Studio 加入了將控制項系結至資料庫、Web 服務和物件中資料的支援。 針對 Word 和 Excel，Visual Studio 加入了執行窗格的支援，可與架構對應檔搭配使用，為您的解決方案建立增強的終端使用者體驗。 如需詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md)。

> [!NOTE]
> 您無法在 Excel 方案中使用多部分 XML 架構。

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>架構附加至 Excel 活頁簿時建立的物件
 當您將架構附加至活頁簿時，Visual Studio 會自動建立數個物件，並將其新增至您的專案。 這些物件不應該使用 Visual Studio 工具刪除，因為它們是由 Excel 所管理。 若要刪除它們，請從工作表移除對應的元素，或使用 Excel 工具卸離架構。

 有兩個主要物件：

- XML 架構 (XSD 檔案) 。 針對活頁簿中的每個架構，Visual Studio 將架構新增至專案。 這會顯示為 **方案總管** 中具有 XSD 擴充功能的專案專案。

- 具型別 <xref:System.Data.DataSet> 類別。 這個類別是根據架構建立的。 這個資料集類別在 **類別檢視** 中是可見的。

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>架構元素對應到 Excel 工作表時建立的物件
 當您將 [ **XML 來源** ] 工作窗格中的架構專案對應至工作表時，Visual Studio 會自動建立數個物件，並將其新增至您的專案：

- 控制。 針對活頁簿中的每個對應物件， <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 會在程式設計模型中建立非重複架構元素) 的控制項 (，或 <xref:Microsoft.Office.Tools.Excel.ListObject> 重複架構專案) 的控制項 (。 <xref:Microsoft.Office.Tools.Excel.ListObject>只有從活頁簿中刪除對應和對應的物件，才能刪除控制項。 如需控制項的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

- BindingSource. 當您透過將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 非重複的架構專案對應至工作表建立時， <xref:System.Windows.Forms.BindingSource> 會建立，並將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項系結至 <xref:System.Windows.Forms.BindingSource> 。 您必須將系結 <xref:System.Windows.Forms.BindingSource> 至符合對應至檔之架構的資料來源實例，例如所建立之具類型類別的實例 <xref:System.Data.DataSet> 。 藉由設定在 <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> [ **屬性** ] 視窗中公開的和屬性，建立系結。

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>不會為物件建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 。 您必須 <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> 在 [ **屬性** ] 視窗中設定和屬性，以手動方式將系結至資料來源。

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office 對應架構和 Visual Studio 資料來源視窗
 [Office] 和 [Visual Studio **資料來源** ] 視窗的對應架構功能，都可協助您在 Excel 工作表上呈現資料以進行報告或編輯。 在這兩種情況下，您都可以將資料元素拖曳到 Excel 工作表上。 這兩種方法都會建立透過資料系結 <xref:System.Windows.Forms.BindingSource> 至資料來源（例如 <xref:System.Data.DataSet> 或 web 服務）的控制項。

> [!NOTE]
> 當您將重複的架構元素對應到工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 。 <xref:Microsoft.Office.Tools.Excel.ListObject>不會自動透過進行系結至資料 <xref:System.Windows.Forms.BindingSource> 。 您必須 <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> 在 [ **屬性** ] 視窗中設定和屬性，以手動方式將系結至資料來源。

 下表顯示這兩種方法之間的部分差異。

|XML 結構描述|資料來源視窗|
|----------------|-------------------------|
|使用 Office 介面。|使用 Visual Studio 中的 [ **資料來源** ] 視窗。|
|啟用內建的 Office 功能，可從 XML 檔案匯入和匯出資料。|您必須以程式設計方式提供匯入和匯出功能。|
|您必須撰寫程式碼，以將資料填入產生的控制項。|從 [ **資料來源** ] 視窗加入的控制項，會在您使用資料庫伺服器時，自動產生程式碼來填入它們，以及所需的連接字串。|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>架構附加至 Word 檔時的行為
 當您將架構附加至檔層級 Office 專案中使用的 Word 檔時，不會建立資料物件。 但是，當您將架構元素對應到您的檔時，就會建立控制項。 控制項的類型取決於您對應的元素類型。重複專案會產生 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項，而非重複的專案則會產生 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。 如需詳細資訊，請參閱 [XMLNodes 控制項](../vsto/xmlnodes-control.md) 和 [XMLNode 控制項](../vsto/xmlnode-control.md)。

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>包含 XML 架構的方案部署
 您應建立安裝程式，以部署使用對應至檔之 XML 架構的解決方案。 安裝程式應在使用者電腦上的架構程式庫中註冊架構。 如果您沒有註冊架構，方案仍會運作，因為 Word 會根據檔中的專案，在使用者開啟時產生暫時的架構。 但是，使用者將無法執行驗證，或儲存用來建立專案的架構。 如需安裝程式的詳細資訊，請參閱 [部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。

 您也可以將程式碼加入至專案，以檢查架構是否在程式庫中並已註冊。 如果不是，您可以警告使用者。

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>另請參閱

- [如何：將架構對應至 Visual Studio 內的 Word 檔](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
