---
title: 使用 ServerDocument 類別管理伺服器上的文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97eed0e4cec143e51195347bfb90d430d8e1eadb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572994"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>使用 ServerDocument 類別管理伺服器上的文件
  您可以使用`ServerDocument`類別[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]管理文件層級自訂的數個部分，即使未安裝 Microsoft Office Word 和 Microsoft Office Excel。 您可以執行下列工作：  
  
-   存取和修改文件或活頁簿的資料快取中的資料。 如需詳細資訊，請參閱[處理文件中的快取資料](#CachedData)。  
  
-   管理文件相關聯的自訂組件。 如需詳細資訊，請參閱[管理文件自訂](#CustomizationInfo)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>了解 ServerDocument 類別  
 `ServerDocument`類別設計用於不需要安裝 Office 的電腦上。 因此，您通常使用這個類別無法與整合與 Office，例如主控台專案或 Windows Form 專案，而不是 Office 專案的應用程式中。 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別*Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*組件。  
  
 `ServerDocument`類別可以用來對使用所建立的文件層級自訂[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]。  
  
 如需有關 Visual Studio 2010 Tools for Office Runtime，以及 Office extensions for.NET Framework，請參閱[Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果您有舊版的應用程式使用`ServerDocument`類別`Visual Studio Tools for Office`system (3.0 版執行階段)、 `Visual Studio Tools for Office` system （3.0 版執行階段） 必須安裝在執行應用程式的電腦上。 `Visual Studio 2010 Tools for Office runtime`無法執行這些應用程式。  
  
##  <a name="CachedData"></a> 處理文件中的快取資料  
 `ServerDocument`類別提供可用來在自訂文件中的資料快取所使用的成員。 如需快取資料的詳細資訊，請參閱[快取資料](../vsto/caching-data.md)和[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出可用來處理快取資料的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷文件是否具有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法|  
|若要存取文件中的快取的資料。<br /><br /> 如需詳細資訊，請參閱[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|  
  
##  <a name="CustomizationInfo"></a> 管理文件自訂  
 您可以使用的成員`ServerDocument`類別以管理與文件相關聯的自訂組件。 比方說，您可以透過程式設計方式移除自訂文件使文件不再是自訂的一部分。  
  
 下表列出可用來管理自訂組件的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷是否將文件是一部分的文件層級自訂。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法|  
|若要以程式設計方式附加至文件在執行階段的自訂。<br /><br /> 如需詳細資訊，請參閱[如何： 附加 managed 程式碼擴充的文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|其中一個<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。|  
|若要在執行階段，以程式設計方式從文件移除自訂。<br /><br /> 如需詳細資訊，請參閱[如何： 移除文件從 managed 程式碼擴充功能](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法|  
|若要取得部署資訊清單與文件相關聯的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 附加 managed 程式碼擴充的文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何： 移除文件從 managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [快取資料](../vsto/caching-data.md)  
  