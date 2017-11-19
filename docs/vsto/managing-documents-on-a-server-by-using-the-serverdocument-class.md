---
title: "使用 ServerDocument 類別管理伺服器上的文件 |Microsoft 文件"
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
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd24d18df965535ee1315ae7807ac23723dc51d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Managing Documents on a Server by Using the ServerDocument Class
  您可以使用 ServerDocument 類別中的[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]管理文件層級自訂的數個部分，即使未安裝 Microsoft Office Word 和 Microsoft Office Excel。 您可以執行下列工作：  
  
-   存取和修改文件或活頁簿的資料快取中的資料。 如需詳細資訊，請參閱[使用的快取資料文件中](#CachedData)。  
  
-   管理文件相關聯的自訂組件。 如需詳細資訊，請參閱[管理文件的自訂](#CustomizationInfo)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>了解 ServerDocument 類別  
 ServerDocument 類別被設計用於不需要安裝 Office 的電腦上。 因此，您通常使用這個類別無法與整合與 Office，例如主控台專案或 Windows Form 專案，而不是 Office 專案的應用程式中。 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 組件中的類別。  
  
 ServerDocument 類別可以用來對使用所建立的文件層級自訂[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]。  
  
 如需有關 Visual Studio 2010 Tools for Office Runtime，以及 Office extensions for.NET Framework，請參閱[Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果您有舊版的應用程式會 ServerDocument 類別 Visual Studio tools for Office system (3.0 版執行階段)，Visual Studio Tools for Office system (3.0 版執行階段) 必須安裝在執行應用程式的電腦上。 Visual Studio 2010 Tools for Office Runtime 無法執行這些應用程式。  
  
##  <a name="CachedData"></a>使用文件中的快取資料  
 ServerDocument 類別可讓您可以使用自訂的文件中的資料快取所使用的成員。 如需快取資料的詳細資訊，請參閱[快取資料](../vsto/caching-data.md)和[存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出可用來處理快取資料的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷文件是否具有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法|  
|若要存取文件中的快取的資料。<br /><br /> 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|  
  
##  <a name="CustomizationInfo"></a>管理文件自訂  
 您可以使用 ServerDocument 類別的成員來管理文件相關聯的自訂組件。 比方說，您可以透過程式設計方式移除自訂文件使文件不再是自訂的一部分。  
  
 下表列出可用來管理自訂組件的成員。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|若要判斷是否將文件是一部分的文件層級自訂。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法|  
|若要以程式設計方式附加至文件自訂執行階段。<br /><br /> 如需詳細資訊，請參閱[如何： 附加 Managed 程式碼擴充的文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|其中一個<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。|  
|若要在執行階段，以程式設計方式從文件移除自訂。<br /><br /> 如需詳細資訊，請參閱[如何： 移除 Managed 程式碼擴充的文件從](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法|  
|若要取得部署資訊清單與文件相關聯的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [如何： 將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何： 從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [快取資料](../vsto/caching-data.md)  
  