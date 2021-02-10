---
title: 部署、發佈、& 升級 SharePoint 方案套件
description: 部署、發行和升級 SharePoint 方案套件。 自訂部署流程。 將封裝發行至遠端或本機伺服器。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd0dfa3a12c675463c46e93aa0d5b25e8b4bd4b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948852"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>部署、發行和升級 SharePoint 方案套件
  在 Visual Studio 開發 SharePoint 方案之後，您可以將其封裝 ( .wsp) 檔部署到本機 SharePoint 伺服器，或將其發行至遠端或本機 SharePoint 伺服器。 如果您部署檔案，您可以自訂部署封裝檔案 ( .wsp) 的方式。

> [!NOTE]
> 目前，只有沙箱化的方案可以發行至遠端 SharePoint 伺服器。 如需詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

## <a name="deploy-publish-and-upgrade"></a>部署、發行和升級
 *部署* 是指將從 sharepoint 專案建立的 sharepoint 方案檔複製到本機主控制項的 Visual Studio。 在已部署的解決方案中，您可以設定部署步驟，例如回收 Internet Information Services (IIS) 集區、在部署後啟用方案等等。 若要部署，請使用 [**組建**] 功能表上的 [**部署**] 命令。 如需詳細資訊，請參閱 [如何：編輯 sharepoint 部署](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 設定和 [如何：將 sharepoint 方案部署和發行至本機 sharepoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。

 *發行* 指的是將沙箱化 SharePoint 方案檔上傳至遠端 SharePoint 網站;亦即，位於另一個系統上的網站。 您也可以將 SharePoint 沙箱化方案檔發行至本機 SharePoint 網站，但不論網站是發佈到本機或遠端，您都無法設定其部署步驟。

 *升級* 指的是更新現有的遠端或本機發佈的 SharePoint 方案。 在 Visual Studio 中對 SharePoint 方案進行任何變更之後，您可以變更方案的封裝檔案名、重新發行方案，然後在成功將後升級解決方案。 如果您重新發佈本機發佈的方案，您可以覆寫現有的方案檔。

## <a name="deploy-packages"></a>部署套件
 您可以將封裝檔案部署到開發電腦上的 SharePoint 伺服器，以進行測試和偵錯工具。 您也可以在 [**發行**] 對話方塊中選擇 [**發行至檔案系統**] 選項按鈕，以建立您可以在另一部電腦上安裝的封裝檔案。 封裝會建立並複製到指定的本機檔案路徑。 若要將 SharePoint 方案部署到本機伺服器，請使用 [**組建**] 功能表上的 [**部署**] 命令。 如需詳細資訊，請參閱 [如何：將 SharePoint 方案部署和發行至本機 sharepoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。

 若要瞭解如何部署清單定義、加入事件接收器，以及使用 [功能設計工具] 和 [封裝設計工具]，請參閱 [逐步解說：部署專案工作清單定義](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。

## <a name="customize-the-deployment-process"></a>自訂部署程式
 下表顯示當您在調試和部署 SharePoint 方案時，可使用的兩個部署設定。

|部署設定|描述|
|------------------------------|-----------------|
|預設|預設部署設定。 執行的部署步驟如下：<br /><br /> 1. 執行預先部署命令。<br />2. 回收 IIS 應用程式集區。<br />3. 撤回方案。<br />4. 新增方案。<br />5. 啟動功能。<br />6. 執行部署後命令。<br /><br /> 卸載套件時，會執行下列撤銷步驟。<br /><br /> 1. 回收 IIS 應用程式集區。<br />2. 撤回方案。|
|沒有啟用|此部署設定會執行與預設設定相同的步驟，但會略過啟用步驟。|

 您可以建立自己的部署設定來完成單一步驟，或在部署程式中變更步驟的順序。 如需詳細資訊，請參閱 [如何：編輯 SharePoint 部署](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)設定。

 您也可以在部署前後新增要執行的命令。 如需詳細資訊，請參閱 [如何：設定 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。

## <a name="publish-packages-to-a-remote-or-local-server"></a>將封裝發行至遠端或本機伺服器
 若要將沙箱化 SharePoint 方案發行至遠端伺服器，請在功能表列上選擇 [ **組建**]、[ **發行**]，然後在 [ **發行** ] 對話方塊中，選擇 [ **發行至 SharePoint 網站** ] 選項按鈕，提供遠端伺服器的 URL，例如 `https://someremoteserver.sharepoint.microsoftonline.com` 。

 若要將 SharePoint 方案發行到本機伺服器，請在 [ **發行** ] 對話方塊中，選擇 [ **發行至檔案系統** ] 選項按鈕，提供本機系統路徑。

 方案成功發佈至 SharePoint 之後，方案會顯示在 **方案庫** 中，您可以在其中啟用此方案。 如需詳細資訊，請參閱 [如何：在遠端伺服器上部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。

### <a name="upgrade-published-packages"></a>升級已發行的封裝
 如果您在發行之後對 Visual Studio 中的 SharePoint 專案進行任何變更，則必須升級已發行的封裝以包含變更。 若要成功升級，套件必須有唯一的名稱。 如果在 SharePoint 網站上找到具有相同名稱的封裝（當您更新現有的應用程式時可能會發生）-錯誤會向您回報檔案名衝突，並可讓您重新命名封裝。 重新發行之後，新的套件會出現在 SharePoint 網站上，並可進行升級。 升級的封裝會使用舊版封裝中的資料來更新方案，然後在 SharePoint 中啟用方案。 如需詳細資訊，請參閱 [如何：在遠端伺服器上部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
