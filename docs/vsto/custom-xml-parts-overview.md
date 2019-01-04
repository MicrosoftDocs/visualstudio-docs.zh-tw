---
title: 自訂 XML 組件概觀
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b0cc9e30cbc55164e8ee993930c6d5fca639a318
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942439"
---
# <a name="custom-xml-parts-overview"></a>自訂 XML 組件概觀
  您可以將 XML 資料嵌入某些 Microsoft Office 應用程式的文件中。 當您將 XML 資料嵌入文件時，該資料就稱為*自訂 XML 組件*。  
  
 您可以使用 Visual Studio 中的 VSTO 增益集或文件層級方案，建立和修改文件中的自訂 XML 組件。 您不必啟動 Microsoft Office 應用程式，即可建立和修改自訂 XML 組件。  
  
 **適用於：** 本主題資訊適用於 Excel、 PowerPoint 和 Word 的 文件層級專案及 VSTO 增益集專案。 如需詳細資訊，請參閱 <<c0> [ 依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
> [!NOTE]  
>  Visual Studio 也可讓您快取文件層級自訂中的資料物件。 雖然這項功能與自訂 XML 組件有些類似，但兩者卻不相同。 如需詳細資訊，請參閱 <<c0> [ 快取文件層級自訂中的資料](../vsto/cached-data-in-document-level-customizations.md)。  
  
## <a name="understand-custom-xml-parts"></a>了解自訂 XML 組件  
 2007 Microsoft Office system 中加入了自訂 XML 組件以及 Open XML 格式。 這些格式包括 Excel、 PowerPoint 和 Word 的新 XML 檔案格式 (例如 *.xlsx*， *.pptx*，並 *.docx*)。 這些格式的文件包含的 XML 檔案 (也稱為*XML 組件*) 組織的 ZIP 封存中的資料夾。 大部分的 XML 組件都是用來協助定義文件結構和狀態的內建組件。 但是，文件也可包含自訂 XML 組件，您可以使用這類自訂 XML 組件在文件中儲存任意 XML 資料。  
  
 啟用應用程式使用的方法，即無法在較舊的二進位檔案格式的文件的 XML 檔案格式 (例如 *.xls*， *.ppt*，並 *.doc*)。 即使未安裝 Microsoft Office，任何可讀取 ZIP 封存的應用程式都可以檢查和修改文件的內容。  
  
 如需 Open XML 和自訂 XML 組件之結構的詳細資訊，請參閱下列文章：  
  
-   [Office (2007) Open XML 檔案格式簡介](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [如何：操作 Open XML 格式的文件](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [逐步解說：Word 2007 XML 格式](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [建置使用 Open XML 格式的 Word 2007 文件](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Excel、Word 和 PowerPoint 也可讓您在以二進位檔案格式儲存的文件中使用自訂 XML 組件。 但是，如果文件是以二進位格式儲存，您就無法在未啟動 Microsoft Office 應用程式的情況下加入或修改自訂 XML 組件。  
  
## <a name="create-and-modify-custom-xml-parts"></a>建立和修改自訂 XML 組件  
 當文件在 Office 應用程式中開啟時，或者當文件為關閉狀態時，即使未安裝 Microsoft Office，您仍可以建立或修改自訂 XML 組件。  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Office 應用程式執行時修改 XML 組件  
 您可以使用的文件層級自訂或 VSTO 增益集，以使用自訂 XML 組件。 如果您使用文件層級自訂，則通常會在自訂的文件中處理自訂 XML 組件。 如果您使用 VSTO 增益集，您可以建立或修改應用程式中開啟任何文件中的自訂 XML 組件。  
  
 若要使用 Visual Studio 建立自訂 XML 組件，請將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 加入文件的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合中。 如需詳細資訊，請參閱下列主題：  
  
-   [如何：將自訂 XML 組件新增至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [如何：使用 VSTO 增益集將自訂 XML 組件新增至文件](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>修改 XML 組件，但不會啟動 Office 應用程式  
 您可以在未啟動 Excel、PowerPoint 或 Word 的情況下，加入或修改自訂 XML 組件。 如果您想要在尚未安裝 Microsoft Office 應用程式的電腦 (例如伺服器) 上處理文件中的 XML 資料，則這種做法會很實用。  
  
 若要在不啟動 Microsoft Office 的情況下加入自訂 XML 組件，請使用 Open XML SDK 中的類別。 這些類別是專為存取 Office 文件特有的 Open XML 內容而設計。 例如，若要將自訂 XML 組件新增至 Excel 活頁簿中，您使用<xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A>方法的<xref:DocumentFormat.OpenXml.Packaging.WorkbookPart>物件。 如需詳細資訊，請參閱 < [Open XML SDK](/office/open-xml/open-xml-sdk)。  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>將自訂 XML 組件繫結至 Word 內容控制項  
 您可以將 Word 方案中的內容控制項繫結至自訂 XML 組件中的項目。 當內容控制項繫結至自訂 XML 組件時，自訂 XML 組件中的資料會顯示在內容控制項的使用者介面 (UI) 中。 如果使用者編輯控制項中的文字，對應的 XML 項目就會自動更新。 同樣地，如果自訂 XML 組件中的項目值變更，繫結至該 XML 項目的內容控制項就會顯示新的資料。 如需詳細資訊，請參閱 <<c0> [ 內容控制項](../vsto/content-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 結構描述和文件層級自訂中的資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [如何：將自訂 XML 組件新增至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [如何：使用 VSTO 增益集將自訂 XML 組件新增至文件](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [內容控制項](../vsto/content-controls.md)   
 [逐步解說：內容控制項繫結至自訂 XML 組件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
