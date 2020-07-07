---
title: 建立和調試 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016357"
---
# <a name="build-and-debug-sharepoint-solutions"></a>建置和偵錯 SharePoint 方案
  一般而言，建立和調試 SharePoint 方案與在中建立和調試其他類型的專案相同 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 本節主題會說明兩者之間的差異。

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 方案的專案輸出
 建立 SharePoint 解決方案會建立元件和方案套件（*.wsp*）檔案。 下表顯示在組建期間這些檔案的位置。

|組建專案|輸出資料夾|
|----------------|-------------------|
|元件、程式資料庫（*.pdb*）和 *.wsp*檔案。|* \<ProjectName> \bin\debug*或* \<ProjectName> \bin\release*|
|SharePoint 專案專案檔案。|* \<ProjectName> \pkg\debug*或* \<ProjectName> \pkg\release*|
|建立中繼檔案。|* \<ProjectName> \obj\debug*或* \<ProjectName> \obj\release*|
|封裝中繼檔案。|* \<ProjectName> \pkgobj\debug*或* \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>建立 SharePoint 方案
 若要建立 SharePoint 方案，開發電腦必須安裝正確的 SharePoint server 版本。 否則，建立 SharePoint 方案與在中建立其他類型的專案相同 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱[如何：建立 SharePoint 方案](../sharepoint/how-to-build-sharepoint-solutions.md)。

## <a name="debug-and-test-sharepoint-solutions"></a>Debug 和 test SharePoint 方案
 在進行調試之前，會 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 *.wsp*封裝複製到 SharePoint 伺服器、啟動網站和 Web 範圍的功能，在某些情況下，會啟動專案。 在某些情況下，您可能需要手動開啟專案。 如需詳細資訊，請參閱[疑難排解 sharepoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)和[Debug sharepoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>使用 Azure DevOps Services 功能來檢查及驗證 SharePoint 方案
 Azure DevOps Services 的功能（例如單元測試和 IntelliTrace）可讓您更精確地找出 SharePoint 方案中的問題。 程式碼剖析可讓您尋找及識別 SharePoint 方案中的效能問題區域。 如需詳細資訊，請參閱[驗證和調試 Sharepoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)和[分析 sharepoint 應用程式的效能](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。

## <a name="security-during-the-build-process"></a>組建過程中的安全性
 若要封裝或部署 SharePoint 方案， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 必須擁有將檔案複製到 sharepoint 伺服器的許可權。 您必須以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 提高許可權的進程身分執行，而且您的使用者帳戶必須是 SharePoint 伺服器上的網站集合管理員。 此外，您必須指定專案是沙箱化方案還是伺服器陣列方案。 如需詳細資訊，請參閱[沙箱與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。

## <a name="using-the-clean-command"></a>使用 Clean 命令
 在 SharePoint 伺服器上安裝 SharePoint 方案以進行偵錯工具時，[**清除**] 命令不會卸載方案。 相反地，您必須透過 SharePoint 設定來停用這些功能。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
