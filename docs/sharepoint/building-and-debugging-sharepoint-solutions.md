---
title: 建置和偵錯 SharePoint 方案 |Microsoft Docs
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
ms.openlocfilehash: 82733a8d3e908e82ad8f841857aa70374495e556
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283531"
---
# <a name="build-and-debug-sharepoint-solutions"></a>建置和偵錯 SharePoint 方案
  一般情況下，建置和偵錯 SharePoint 方案等同於建置和偵錯其他類型的專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 本節主題會說明兩者之間的差異。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 方案的專案輸出
 建置 SharePoint 解決方案建立組件及方案套件 (*.wsp*) 檔案。 下表顯示這些檔案的位置，在建置期間。  
  
|建立項目|輸出資料夾|  
|----------------|-------------------|  
|組件、 程式資料庫 (*.pdb*)，以及 *.wsp*檔案。|*\<專案名稱 > \bin\debug*或是*\<專案名稱 > \bin\release*|  
|SharePoint 專案項目檔案。|*\<專案名稱 > \pkg\debug*或是*\<專案名稱 > \pkg\release*|  
|建立中繼檔案。|*\<專案名稱 > \obj\debug*或是*\<專案名稱 > \obj\release*|  
|中繼套件的檔案。|*\<專案名稱 > \pkgobj\debug*或是*\<專案名稱 > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>建置 SharePoint 解決方案
 若要建置 SharePoint 解決方案，在開發電腦必須安裝的 SharePoint 伺服器的正確版本。 否則，建置 SharePoint 解決方案是建置中專案的其他類型相同[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 如何： 建置 SharePoint 解決方案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## <a name="debug-and-test-sharepoint-solutions"></a>偵錯及測試 SharePoint 方案
 偵錯前,[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]複本 *.wsp*封裝到 SharePoint 伺服器，啟動站台和 Web 範圍的功能，並在某些情況下，會啟動專案。 在某些情況下，您可能需要手動開啟專案。 如需詳細資訊，請參閱 <<c0> [ 疑難排解 SharePoint 解決方案](../sharepoint/troubleshooting-sharepoint-solutions.md)並[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>偵錯，並使用 Azure DevOps 服務功能，以驗證 SharePoint 方案
 單元測試和 IntelliTrace 等的 azure DevOps 服務功能可讓您更精確地找出 SharePoint 方案中的問題。 程式碼剖析可讓您尋找及識別 SharePoint 方案中的效能問題區域。 如需詳細資訊，請參閱 <<c0> [ 驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)並[效能 SharePoint 應用程式程式碼剖析](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## <a name="security-during-the-build-process"></a>建置程序期間的安全性
 封裝或部署 SharePoint 方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]必須將檔案複製到 SharePoint 伺服器的權限。 您必須執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提升權限的程序，以及您的使用者帳戶必須是 SharePoint 伺服器上的網站集合管理員。 此外，您必須指定您的專案是否為沙箱化方案 」 或 「 伺服器陣列方案。 如需詳細資訊，請參閱 < [Differences Between Sandboxed and Farm 解決方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="using-the-clean-command"></a>使用 [清除] 命令  
 SharePoint 方案進行偵錯，在 SharePoint 伺服器上安裝時**清除**命令不會解除安裝方案。 相反地，您必須停用透過 SharePoint 設定的功能。  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [瀏覽 SharePoint 連線，使用 伺服器總管](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 
