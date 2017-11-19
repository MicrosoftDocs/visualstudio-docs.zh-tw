---
title: "建置和偵錯 SharePoint 方案 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7582b0bcef8a97de14fb3b931745d6dcc21fa876
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="building-and-debugging-sharepoint-solutions"></a>建置和偵錯 SharePoint 方案
  一般而言，建置和偵錯 SharePoint 方案等同於建置和偵錯其他類型的專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 本節主題會說明兩者之間的差異。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 方案的專案輸出  
 建置 SharePoint 解決方案，會建立組件和方案套件 (.wsp) 檔案。 下表顯示這些檔案的位置，在建置期間。  
  
|建立項目|輸出資料夾|  
|----------------|-------------------|  
|組件、 程式資料庫 (PDB) 和.wsp 檔案。|*ProjectName*\bin\debug 或*ProjectName*\bin\release|  
|SharePoint 專案項目檔案。|*ProjectName*\pkg\debug 或*ProjectName*\pkg\release|  
|建立中繼檔案。|*ProjectName*\obj\debug 或*ProjectName*\obj\release|  
|套件中繼檔案。|*ProjectName*\pkgobj\debug 或*ProjectName*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>建立 SharePoint 方案  
 若要建置 SharePoint 解決方案，在開發電腦必須安裝 SharePoint server 的正確版本。 否則，請建置 SharePoint 解決方案等同於建立其他類型的專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[How to： 建立 SharePoint 方案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>偵錯和測試 SharePoint 方案  
 偵錯之前， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .wsp 將封裝複製到 SharePoint 伺服器、 網站和 Web 範圍的功能，就會啟動，在某些情況下，啟動 專案。 在某些情況下，您可能需要手動開啟專案。 如需詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)和[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>使用 ALM 功能偵錯及驗證 SharePoint 方案  
 Visual Studio ALM 功能 (例如單元測試和 IntelliTrace) 可讓您更精確地找出 SharePoint 方案中的問題。 程式碼剖析可讓您尋找及識別 SharePoint 方案中的效能問題區域。 如需詳細資訊，請參閱[驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)和[效能 SharePoint 應用程式程式碼剖析](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## <a name="security-during-the-build-process"></a>建置程序期間的安全性  
 封裝或部署 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]必須將檔案複製到 SharePoint 伺服器的權限。 您必須執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提升權限的程序，以及您的使用者帳戶必須是網站集合管理員，在 SharePoint 伺服器上。 此外，您必須指定專案是否為沙箱化方案或伺服器陣列方案。 如需詳細資訊，請參閱[沙箱之間的差異與伺服器陣列方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="using-the-clean-command"></a>使用 [清除] 命令  
 SharePoint 方案進行偵錯，在 SharePoint 伺服器上安裝時**清除**命令不會解除安裝方案。 相反地，您必須停用透過 SharePoint 組態功能。  
  
## <a name="see-also"></a>另請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [使用 伺服器總管瀏覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  