---
title: 建置和偵錯 SharePoint 方案 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d0bc3185b0684f96bf31cc127cd852448afe772
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765066"
---
# <a name="build-and-debug-sharepoint-solutions"></a>建置和偵錯 SharePoint 方案
  一般而言，建置和偵錯 SharePoint 方案等同於建置和偵錯其他類型的專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 本節主題會說明兩者之間的差異。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 方案的專案輸出
 建置 SharePoint 解決方案建立組件和方案套件 (*.wsp*) 檔案。 下表顯示這些檔案的位置，在建置期間。  
  
|建立項目|輸出資料夾|  
|----------------|-------------------|  
|組件、 程式資料庫 (*.pdb*)，和 *.wsp*檔案。|*{ProjectName} \bin\debug*或 *{ProjectName} \bin\release*|  
|SharePoint 專案項目檔案。|*{ProjectName} \pkg\debug*或 *{ProjectName} \pkg\release*|  
|建立中繼檔案。|*{ProjectName} \obj\debug*或 *{ProjectName} \obj\release*|  
|套件中繼檔案。|*{ProjectName} \pkgobj\debug*或 *{ProjectName} \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>建立 SharePoint 方案
 若要建置 SharePoint 解決方案，在開發電腦必須安裝 SharePoint server 的正確版本。 否則，請建置 SharePoint 解決方案等同於建立其他類型的專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[How to： 建立 SharePoint 方案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## <a name="debug-and-test-sharepoint-solutions"></a>偵錯和測試 SharePoint 方案
 偵錯之前，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]複本 *.wsp*封裝到 SharePoint 伺服器，會啟用網站和 Web 範圍的功能，並在某些情況下，啟動專案。 在某些情況下，您可能需要手動開啟專案。 如需詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)和[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>偵錯並使用 ALM 功能驗證 SharePoint 方案
 Visual Studio ALM 功能 (例如單元測試和 IntelliTrace) 可讓您更精確地找出 SharePoint 方案中的問題。 程式碼剖析可讓您尋找及識別 SharePoint 方案中的效能問題區域。 如需詳細資訊，請參閱[驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)和[效能 SharePoint 應用程式程式碼剖析](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## <a name="security-during-the-build-process"></a>建置程序期間的安全性
 封裝或部署 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]必須將檔案複製到 SharePoint 伺服器的權限。 您必須執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提升權限的程序，以及您的使用者帳戶必須是網站集合管理員，在 SharePoint 伺服器上。 此外，您必須指定專案是否為沙箱化方案或伺服器陣列方案。 如需詳細資訊，請參閱[沙箱之間的差異與伺服器陣列方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="using-the-clean-command"></a>使用 [清除] 命令  
 SharePoint 方案進行偵錯，在 SharePoint 伺服器上安裝時**清除**命令不會解除安裝方案。 相反地，您必須停用透過 SharePoint 組態功能。  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [使用 伺服器總管瀏覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 