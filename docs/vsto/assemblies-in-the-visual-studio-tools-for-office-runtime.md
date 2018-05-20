---
title: 在 Visual Studio Tools for Office runtime 的組件
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ff32d472d0e2005b22acb8d751e03c6aa3f61ef
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>在 Visual Studio Tools for Office runtime 的組件
  當您建立 Office 專案時，Visual Studio 會自動針對專案類型和專案的目標 .NET Framework，加入適用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 組件的參考。 適用於 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 擴充功能包含不同的組件。 如需 Office 擴充功能的詳細資訊，請參閱[Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Office extensions for.NET Framework 4 中的組件， [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 下表列出適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 擴充功能隨附的組件。 如需命名空間和類型，這些組件中的文件，請參閱[受管理參考&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|提供下列類型：<br /><br /> -用於建立功能區自訂和智慧標籤的型別。 **注意：** 智慧標籤已被取代[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]和[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。<br />-文件層級自訂和自訂工作窗格在 VSTO 增益集中建立執行窗格的型別。|  
|Microsoft.Office.Tools.Excel.dll|提供代表 Excel 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類型。|  
|Microsoft.Office.Tools.Word.dll|提供代表 Word 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|提供下列類型：<br /><br /> -由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-屬性您可以使用時建立 Outlook 表單區域。|  
|Microsoft.Office.Tools.dll|提供屬於 Visual Studio Tools for Office Runtime 基礎結構，而且不適合直接從程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性和<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>介面，您可以使用快取中的文件層級自訂的資料物件。 如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。<br />-<xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>介面，您可以實作以執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。<br />-由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，將自訂組件附加至文件，並存取文件中快取的資料，您可以使用。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別所代表的階層快取文件層級自訂中的資料。 如需詳細資訊，請參閱[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|  
  
 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 為目標的專案還會參考下列組件。 這些組件不是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可轉散發套件的一部分， 而是必須隨方案一起部署的相依組件。 根據預設，這些組件會複製到專案的組建輸出資料夾 (當這些組件的 [複製到本機]  屬性設定為 [True] 時)。 如果使用 ClickOnce 部署專案，這些組件會包含在產生的套件中。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|提供 VSTO 增益集專案中產生之 `ThisAddIn` 類別的基底類別，以及所有專案中產生之功能區類別的基底類別。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|提供下列類型：<br /><br /> -基底類別所產生`ThisWorkbook`和`Sheet`中的類別文件層級的專案適用於 Excel。<br />您可以使用 Excel 專案中的工作表的 Windows Form 控制項。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|提供 Outlook 專案中產生之 `ThisAddIn` 和表單區域類別的基底類別。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|提供下列類型：<br /><br /> -基底類別所產生的`ThisDocument`Word 的文件層級專案中的類別。<br />您可以使用 Word 專案中的文件的 Windows Form 控制項。|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>適用於.NET Framework 3.5 的 Office 擴充功能中的組件  
 下表列出適用於 .NET Framework 3.5 的 Office 擴充功能隨附的組件。 如需命名空間和類別，這些組件中的文件，請參閱 Visual Studio 2008 文件中的下列參考章節： [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|提供下列類型：<br /><br /> -Microsoft.Office.Tools.AddIn 基底類別的 VSTO 增益集。<br />-用於建立功能區自訂和智慧標籤的類別。 **注意：** 智慧標籤已被取代[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]和[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。<br />-文件層級自訂和自訂工作窗格在 VSTO 增益集中建立執行窗格的類別。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|提供 Excel 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類別。|  
|Microsoft.Office.Tools.Word.v9.0.dll|提供 Word 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v9.0.dll|提供下列類型：<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90))類別，可提供資料繫結功能的主控制項在文件層級自訂。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性和<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>介面，您可以使用快取中的文件層級自訂的資料物件。 如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。<br />-由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|提供 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面，您可以實作這個介面來執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[進階 Office 方案部署](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02)。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，您可以使用程式設計方式將自訂組件附加至文件，並存取文件中快取的資料。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別所代表的階層快取文件層級自訂中的資料。 如需詳細資訊，請參閱[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|提供下列類型：<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry 和 Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList 類別，可用來建立使用者內含清單項目，授與信任給 Office.NET Framework 3.5 為目標的解決方案。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  