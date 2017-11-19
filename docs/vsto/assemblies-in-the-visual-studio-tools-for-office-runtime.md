---
title: "中的 Visual Studio Tools for Office Runtime 的組件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Visual Studio Tools for Office runtime, assemblies
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 130cf43e7c11eeccae8fdbdd22b46faf6bfe3c49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime 的組件
  當您建立 Office 專案時，Visual Studio 會自動針對專案類型和專案的目標 .NET Framework，加入適用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 組件的參考。 適用於 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 擴充功能包含不同的組件。 如需 Office 擴充功能的詳細資訊，請參閱 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>適用於 .NET Framework 4 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 擴充功能中的組件  
 下表列出適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Office 擴充功能隨附的組件。 如需命名空間和類型，這些組件中的文件，請參閱[Managed 參考 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/managed-reference-office-development-in-visual-studio.md)。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|提供下列類型：<br /><br /> -用於建立功能區自訂和智慧標籤的型別。 **注意：**智慧標籤已被取代[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]和[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。<br />-文件層級自訂和自訂工作窗格在 VSTO 增益集中建立執行窗格的型別。|  
|Microsoft.Office.Tools.Excel.dll|提供代表 Excel 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類型。|  
|Microsoft.Office.Tools.Word.dll|提供代表 Word 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|提供下列類型：<br /><br /> -由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-屬性您可以使用時建立 Outlook 表單區域。|  
|Microsoft.Office.Tools.dll|提供屬於 Visual Studio Tools for Office Runtime 基礎結構，而且不適合直接從程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性和<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>介面，您可以使用快取中的文件層級自訂的資料物件。 如需詳細資訊，請參閱 [Caching Data](../vsto/caching-data.md)。<br />-<xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>介面，您可以實作以執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[部署 Office 方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。<br />-由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，將自訂組件附加至文件，並存取文件中快取的資料，您可以使用。 如需詳細資訊，請參閱 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別所代表的階層快取文件層級自訂中的資料。 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。|  
  
 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 為目標的專案還會參考下列組件。 這些組件不是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可轉散發套件的一部分， 而是必須隨方案一起部署的相依組件。 根據預設，這些組件會複製到專案的組建輸出資料夾 (當這些組件的 [複製到本機]  屬性設定為 [True] 時)。 如果使用 ClickOnce 部署專案，這些組件會包含在產生的套件中。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|提供 VSTO 增益集專案中產生之 `ThisAddIn` 類別的基底類別，以及所有專案中產生之功能區類別的基底類別。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|提供下列類型：<br /><br /> -基底類別所產生`ThisWorkbook`和`Sheet`中的類別文件層級的專案適用於 Excel。<br />您可以使用 Excel 專案中的工作表的 Windows Form 控制項。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|提供 Outlook 專案中產生之 `ThisAddIn` 和表單區域類別的基底類別。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|提供下列類型：<br /><br /> -基底類別所產生的`ThisDocument`Word 的文件層級專案中的類別。<br />您可以使用 Word 專案中的文件的 Windows Form 控制項。|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>適用於 .NET Framework 3.5 的 Office 擴充功能中的組件  
 下表列出適用於 .NET Framework 3.5 的 Office 擴充功能隨附的組件。 如需這些組件中之命名空間和類別的相關文件，請參閱 Visual Studio 2008 文件中的下列參考章節： [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
|組件名稱|描述|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|提供下列類型：<br /><br /> -Microsoft.Office.Tools.AddIn 基底類別的 VSTO 增益集。<br />-用於建立功能區自訂和智慧標籤的類別。 **注意：**智慧標籤已被取代[!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]和[!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。<br />-文件層級自訂和自訂工作窗格在 VSTO 增益集中建立執行窗格的類別。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|提供 Excel 方案的主項目和主控制項。 如需詳細資訊，請參閱 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類別。|  
|Microsoft.Office.Tools.Word.v9.0.dll|提供 Word 方案的主項目和主控制項。 如需詳細資訊，請參閱 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v9.0.dll|提供下列類型：<br /><br /> -Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent 類別，提供文件層級自訂中主控制項的資料繫結功能。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|提供下列類型：<br /><br /> -Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute 屬性和 Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType 介面，您可以使用快取中的文件層級自訂的資料物件。 如需詳細資訊，請參閱 [Caching Data](../vsto/caching-data.md)。<br />-由 Visual Studio Tools for Office runtime 可能擲回的例外狀況。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|提供 Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction 介面中，您可以實作以執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱 [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02)。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|提供下列類型：<br /><br /> 您可以使用程式設計方式將自訂組件附加至文件，並存取文件中的快取的資料-microsoft.visualstudio.tools.applications.serverdocument 的參考類別。 如需詳細資訊，請參閱 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別所代表的階層快取文件層級自訂中的資料。 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|提供下列類型：<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry 和 Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList 類別，可用來建立使用者內含清單項目，授與信任給 Office.NET Framework 3.5 為目標的解決方案。<br />-其他屬於 Visual Studio Tools for Office runtime 基礎結構，但不適合直接從您的程式碼使用的類型。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office Runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  