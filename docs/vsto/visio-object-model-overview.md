---
title: Visio 物件模型概觀 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e77256d800cb23b61a6680cdf59e60a39c7b57e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visio-object-model-overview"></a>Visio 物件模型概觀
  若要開發 Microsoft Office Visio 的 Office 方案，您可以與 Visio 物件模型互動。 此物件模型是由類別和介面，提供 Visio 主要 interop 組件，而且 Microsoft.Office.Interop.Visio 命名空間中定義所組成。  
  
 本主題提供簡短的 Visio 物件模型概觀。 如需使用 Visio 物件模型在 Office 專案中執行工作的詳細資訊，請參閱下列主題：  
  
-   [使用 Visio 文件](../vsto/working-with-visio-documents.md)  
  
-   [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)  
  
## <a name="understanding-the-visio-object-model"></a>了解 Visio 物件模型  
 Visio 會提供許多您可以與之互動的物件。 這些物件是在密切遵循使用者介面的階層內組合管理。 階層的頂端是 [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx) 物件。 這個物件代表 Visio 目前的執行個體。 Microsoft.Office.Interop.Visio.Application 物件包含的 Microsoft.Office.Interop.Visio.Document 和 Microsoft.Office.Interop.Visio.Page 物件，以及 Microsoft.Office.Interop.Visio.Documents 和Microsoft.Office.Interop.Visio.Pages 集合。 這些物件和集合每個都有許多方法和屬性，您可以存取操作並與之互動。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx)、 [Microsoft.Office.Interop.Visio.Document](https://msdn.microsoft.com/library/office/ff765575.aspx)和 [Microsoft.Office.Interop.Visio.Page](https://msdn.microsoft.com/library/office/ff767035.aspx) 物件，以及 [Microsoft.Office.Interop.Visio.Documents](https://msdn.microsoft.com/library/office/ff768812.aspx) 和 [Microsoft.Office.Interop.Visio.Pages](https://msdn.microsoft.com/library/office/ff766165.aspx) 集合的 VBA 參考文件。  
  
 下列各節簡述最上層物件，以及它們彼此之間的互動方式。 這些物件包含下列物件：  
  
-   Application 物件  
  
-   Document 物件  
  
-   Page 物件  
  
### <a name="application-object"></a>Application 物件  
 Microsoft.Office.Interop.Visio.Application 物件代表 Visio 應用程式中，而且是所有其他物件的父系。 其成員通常會整體套用至 Visio。 您可以使用的屬性和 Microsoft.Office.Interop.Visio.Application 和 Microsoft.Office.Interop.Visio.ApplicationSettings 物件的方法來控制 Visio 環境。  
  
 在 VSTO 增益集專案中，您可以透過存取 Microsoft.Office.Interop.Visio.Application 物件`Application`欄位`ThisAddIn`類別。 如需詳細資訊，請參閱 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
### <a name="document-object"></a>Document 物件  
 Microsoft.Office.Interop.Visio.Document 物件是 visio 程式設計的核心的核心。 它代表繪圖、樣板或範本檔案。 當您開啟 Visio 文件或建立新的文件時，您會建立新的 Microsoft.Office.Interop.Visio.Document 物件，它會加入到 Microsoft.Office.Interop.Visio.Documents Microsoft.Office.Interop.Visio.Application 物件集合.  
  
 具有焦點的文件稱為使用中文件。 它會以 Microsoft.Office.Interop.Visio.Application.ActiveDocument Microsoft.Office.Interop.Visio.Application 物件屬性。  
  
### <a name="page-object"></a>Page 物件  
 Microsoft.Office.Interop.Visio.Page 物件代表前景頁面或背景頁面的繪圖區域。 您可以使用 Microsoft.Office.Interop.Visio.Page.Background 屬性來判斷頁面為前景或背景頁面。  
  
 若要建立圖形，您可以使用包含 Microsoft.Office.Interop.Visio.Page.DrawSpline 和 Microsoft.Office.Interop.Visio.Page.DrawOval 方法的方法。 此外，您可以從樣板擷取主圖形，並使用 Microsoft.Office.Interop.Visio.Page.Drop 或 Microsoft.Office.Interop.Visio.Page.DropMany 方法，將圖形放在頁面上。  
  
## <a name="using-the-visio-object-model-documentation"></a>使用 Visio 物件模型文件  
 如需 Visio 物件模型的完整資訊，您可以參考 Visio VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 Visual 物件模型。 如需詳細資訊，請參閱 [Visio 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199775)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 Visio 主要 Interop 組件 (PIA) 中的類型和成員。 例如，VBA 物件模型參考中的文件物件對應至 Visio PIA 中 Microsoft.Office.Interop.Visio.Document 型別。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Visio VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C# 程式碼。  
  
> [!NOTE]  
>  目前沒有 Visio 主要 Interop 組件的參考文件。  
  
 如需相關程式碼範例及其他建立 Visio 解決方案的工具，請參閱 [Visio 2010 軟體開發套件](http://go.microsoft.com/fwlink/?LinkId=196501)。  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>主要 Interop 組件中的其他類型  
 因為實作差異之故，您可以在主要 Interop 組件中找到對 VBA 不可見的類型。 VBA 提供檢視 Visio 物件模型，內含您可直接使用的物件和成員。 主要 Interop 組件會公開相同的物件模型，但也包含其他介面、類別和成員，可將 COM 物件模型中的物件轉譯成 managed 程式碼。 這些額外的項目不宜直接在程式碼中使用。  
  
 如需詳細資訊，請參閱 [Office 主要 Interop 組件中的類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=189592) 和 [Office Primary Interop Assemblies](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [使用 Visio 文件](../vsto/working-with-visio-documents.md)   
 [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)  
  
  