---
title: 部署、 發佈及升級 SharePoint 方案套件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebe207bffe16ef7b8dc7af5a79c01b3ee74abe3f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863275"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>部署、 發行和升級 SharePoint 方案套件
  開發 Visual Studio 中的 SharePoint 方案之後，您可以將其套件 (.wsp) 檔案部署至本機 SharePoint 伺服器，或將它發佈至遠端或本機 SharePoint 伺服器。 如果您部署的檔案時，您可以自訂部署的封裝檔案 (.wsp) 的方式。  
  
> [!NOTE]  
>  目前，只有沙箱化方案可以發行至 SharePoint 的遠端伺服器。 如需詳細資訊，請參閱 <<c0> [ 沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
## <a name="deploy-publish-and-upgrade"></a>部署、 發行和升級
 *部署*指的是複製到本機主機從 Visual Studio 中 SharePoint 專案建置 SharePoint 方案檔。 在已部署的解決方案中，您可以設定的部署步驟，例如回收網際網路資訊服務 (IIS) 集區中，在部署後，啟用解決方案等等。 若要部署，請使用**Deploy**命令**建置**功能表。 如需詳細資訊，請參閱[＜How to：編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)和[How to:部署並發佈至本機 SharePoint 網站的 SharePoint 方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 *發行*是指將沙箱化 SharePoint 方案檔上傳至遠端 SharePoint 網站，也就是位於另一個系統上的站台。 您也可以發佈 SharePoint 沙箱化方案檔案至本機 SharePoint 網站，但不論發佈至站台是本機或遠端，您不能設定它的部署步驟。  
  
 *升級*指的是更新現有的遠端或在本機上已發行的 SharePoint 方案。 對 SharePoint 方案在 Visual Studio 中進行任何變更之後，您會變更方案的套件檔案名稱、 重新發行方案，然後再升級解決方案之後順利重新發行。 如果您重新發佈已在本機發行的方案時，您可以覆寫現有的方案檔。  
  
## <a name="deploy-packages"></a>部署封裝
 您可以部署到 SharePoint 伺服器的封裝檔案在開發電腦進行測試和偵錯。 您也可以建立封裝檔，您可以安裝在另一部電腦上，選擇**發行至檔案系統**選項按鈕**發佈** 對話方塊。 建立封裝，並複製到指定的本機檔案路徑。 若要將 SharePoint 方案部署到本機伺服器中，使用**Deploy**命令**建置**功能表。 如需詳細資訊，請參閱[＜How to：部署並發佈至本機 SharePoint 網站的 SharePoint 方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 若要了解如何部署清單定義、 加入事件接收器，以及使用的功能設計工具和封裝設計工具，請參閱[逐步解說：部署專案工作清單定義](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。  
  
## <a name="customize-the-deployment-process"></a>自訂部署程序
 下表顯示偵錯和部署 SharePoint 方案時，您可以使用兩個部署組態。  
  
|部署組態|描述|  
|------------------------------|-----------------|  
|預設|部署組態的預設值。 執行下列的部署步驟：<br /><br /> 1.執行預先部署命令。<br />2.回收 IIS 應用程式集區。<br />3.撤銷方案。<br />4.新增解決方案。<br />5.啟用功能。<br />6.執行部署後命令。<br /><br /> 解除安裝封裝時，請執行下列的撤銷步驟。<br /><br /> 1.回收 IIS 應用程式集區。<br />2.撤銷方案。|  
|無法啟動|此部署組態會以預設組態中，執行相同的步驟，但會略過啟用步驟。|  
  
 您可以建立您自己的部署組態，以完成單一步驟或變更的部署程序中的步驟順序。 如需詳細資訊，請參閱[＜How to：編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  

 您也可以新增要在部署前後執行的命令。 如需詳細資訊，請參閱[＜How to：設定 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。  
  
## <a name="publish-packages-to-a-remote-or-local-server"></a>將套件發佈到遠端或本機伺服器
 若要將沙箱化 SharePoint 方案發行至遠端伺服器，在功能表列上，選擇**建置**，**發佈**，然後在**發行**對話方塊方塊中，選擇  **發行至 SharePoint 網站**選項按鈕，提供遠端伺服器的 URL，例如 **https://someremoteserver.sharepoint.microsoftonline.com** 。  
  
 在發行至本機伺服器、 SharePoint 方案**發佈**對話方塊方塊中，選擇**發行至檔案系統**選項按鈕，提供本機系統路徑。  
  
 方案已成功發行到 SharePoint 之後，解決方案會出現在**解決方案資源庫**其中，您可以啟用它。 如需詳細資訊，請參閱[＜How to：部署、 發行和升級 SharePoint 方案，在遠端伺服器上的](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
### <a name="upgrade-published-packages"></a>升級發佈的封裝
 如果您在 Visual Studio 中 SharePoint 專案上進行了任何變更發行後，已發佈的封裝必須升級為包含所做的變更。 若要順利升級，封裝必須有唯一的名稱。 如果具有相同名稱的封裝上找到 SharePoint 站台-您要更新現有的應用程式時可能發生的錯誤警示您的檔案名稱發生衝突，並可讓您重新命名封裝。 之後重新發行，新的封裝會在 SharePoint 網站上會出現，而且可以升級。 升級的封裝會使用較舊的封裝中，資料會更新方案，，然後啟動 SharePoint 中的解決方案。 如需詳細資訊，請參閱[＜How to：部署、 發行和升級 SharePoint 方案，在遠端伺服器上的](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## <a name="see-also"></a>另請參閱
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
