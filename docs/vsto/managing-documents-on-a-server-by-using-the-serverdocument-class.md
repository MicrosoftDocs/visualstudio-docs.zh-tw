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
ms.openlocfilehash: e983f4cf1b90150113fcfa33702d85bb41a30924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939133"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>使用 ServerDocument 類別管理伺服器上的文件
  您可以使用`ServerDocument`類別中[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]管理文件層級自訂的數個層面，即使未安裝 Microsoft Office Word 和 Microsoft Office Excel。 您可以執行下列工作：  
  
- 存取和修改文件或活頁簿的資料快取中的資料。 如需詳細資訊，請參閱 <<c0> [ 文件中的快取資料搭配使用](#CachedData)。  
  
- 管理文件相關聯的自訂組件。 如需詳細資訊，請參閱 <<c0> [ 管理文件自訂](#CustomizationInfo)。  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>了解 ServerDocument 類別  
 `ServerDocument`類別設計來在未安裝 Office 的電腦上使用。 因此，您通常使用這個類別中未整合 Office，例如主控台專案或 Windows Form 專案，而不是 Office 專案的應用程式。 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別內*Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*組件。  
  
 `ServerDocument`類別可以用來對使用所建立的文件層級自訂[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]。  
  
 如需 Visual Studio 2010 Tools for Office Runtime 以及 Office 擴充功能適用於.NET Framework，請參閱 < [Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果您有使用的舊版應用程式`ServerDocument`類別內`Visual Studio Tools for Office`system (3.0 版執行階段)，則`Visual Studio Tools for Office`system （3.0 版執行階段） 必須安裝在執行應用程式的電腦上。 `Visual Studio 2010 Tools for Office runtime`無法執行這些應用程式。  
  
##  <a name="CachedData"></a> 使用文件中的快取資料  
 `ServerDocument`類別提供可用來在自訂文件中的資料快取所使用的成員。 如需有關快取資料的詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)並[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出您可以使用快取的資料搭配使用的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷文件是否具有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法|  
|若要存取文件中快取的資料。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 存取在伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|  
  
##  <a name="CustomizationInfo"></a> 管理文件自訂  
 您可以使用的成員`ServerDocument`類別來管理文件相關聯的自訂組件。 比方說，您可以以程式設計方式移除自訂文件，因此文件不再是自訂的一部分。  
  
 下表列出可用來管理自訂組件的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷是否在文件。 文件層級自訂一部分|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法|  
|若要以程式設計方式將自訂附加至在執行階段的文件。<br /><br /> 如需詳細資訊，請參閱[如何： 附加 managed 程式碼擴充的文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|其中一個<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。|  
|若要在執行階段，以程式設計方式從文件移除自訂。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 如何： 移除文件從 managed 程式碼擴充功能](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法|  
|若要取得部署資訊清單與文件相關聯的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 附加 managed 程式碼擴充的文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何： 移除文件從 managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [快取資料](../vsto/caching-data.md)  
  