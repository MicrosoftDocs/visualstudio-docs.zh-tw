---
title: 部署、發佈、&升级 SharePoint 解決方案包
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
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444966"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>部署、發佈和升級 SharePoint 解決方案套件
  在 Visual Studio 中開發 SharePoint 解決方案後,可以將其包 (.wsp) 檔部署到本地 SharePoint 伺服器,也可以將其發布到遠端或本地 SharePoint 伺服器。 如果部署這些檔,則可以自定義包檔的部署方式。

> [!NOTE]
> 目前,只能將沙盒解決方案發佈到遠端 SharePoint 伺服器。 有關詳細資訊,請參閱[沙箱解決方案注意事項](../sharepoint/sandboxed-solution-considerations.md)。

## <a name="deploy-publish-and-upgrade"></a>部署、發佈和升級
 *部署*是指將從 Visual Studio 中的 SharePoint 專案生成的 SharePoint 解決方案檔複製到本地主機。 在已部署的解決方案中,可以配置部署步驟,例如回收 Internet 資訊服務 (IIS) 池、部署後啟動解決方案等。 要進行部署,請使用 **「生成**」功能表上的 **「部署」** 命令。 有關詳細資訊,請參閱[如何:編輯 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)以及如何[:將 SharePoint 解決方案部署到本地 SharePoint 站點並將其發表到](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。

 *發佈*是指將沙箱的 SharePoint 解決方案檔上載到遠端 SharePoint 網站;即位於另一個系統上的網站。 您還可以將 SharePoint 沙箱解決方案檔發佈到本地 SharePoint 站點,但無論發佈到網站是本地網站還是遠端網站,您都無法配置其部署步驟。

 *升級*是指更新現有的遠端或本地發佈的 SharePoint 解決方案。 對 Visual Studio 中的 SharePoint 解決方案進行任何更改後,可以更改解決方案的包檔名,重新發表解決方案,然後在成功重新發表解決方案後升級解決方案。 如果重新發佈本地發佈的解決方案,則可以覆蓋現有解決方案檔。

## <a name="deploy-packages"></a>部署套件
 您可以將包檔部署到開發電腦上的 SharePoint 伺服器以進行測試和調試。 您還可以透過「**發布到檔案系統」** 對話框中的「發布到檔案系統」選項按鈕建立可以在另一台電腦上安裝的套件檔**Publish**。 將建立包並將其複製到指定的本地檔案路徑。 要將 SharePoint 解決方案部署到本地伺服器,請使用 **「生成**」功能表上的 **「部署」** 命令。 有關詳細資訊,請參閱[如何:將 SharePoint 解決方案部署到本地 SharePoint 網站並將其發表到](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。

 要瞭解如何部署清單定義、新增事件接收器以及使用功能設計器和套件設計器,請參閱[演練:部署專案工作列表定義](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。

## <a name="customize-the-deployment-process"></a>自訂部署程序
 下表顯示了在調試和部署 SharePoint 解決方案時可以使用的兩種部署配置。

|部署設定|描述|
|------------------------------|-----------------|
|預設|默認部署配置。 執行以下部署步驟:<br /><br /> 1. 運行部署前命令。<br />2. 回收 IIS 應用程式池。<br />3. 縮迴溶液。<br />4. 添加解決方案。<br />5. 啟動功能。<br />6. 運行部署後命令。<br /><br /> 卸載包時,將執行以下撤回步驟。<br /><br /> 1. 回收 IIS 應用程式池。<br />2. 縮迴溶液。|
|沒有啟動|此部署配置運行的步驟與預設配置相同,但跳過啟動步驟。|

 您可以創建自己的部署配置以完成單步驟或更改部署過程中步驟的順序。 有關詳細資訊,請參閱[如何:編輯 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。

 您還可以添加要在部署之前和之後運行的命令。 有關詳細資訊,請參閱[如何:設置 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。

## <a name="publish-packages-to-a-remote-or-local-server"></a>將套件發布到遠端或本地端伺服器
 要將沙箱的 SharePoint 解決方案發布到遠端伺服器,請選擇選單列上的 **「產生**」、「**發布**」,然後在 **「發布」** 對話框中選擇「**發布到 SharePoint 網站**」`https://someremoteserver.sharepoint.microsoftonline.com`選項按鈕,提供遠端伺服器的 URL,如 。

 要將 SharePoint 解決方案發布到本地伺服器,請在 **「發布」** 對話方塊中選擇「**發布到檔案系統**」選項按鈕,提供本地系統路徑。

 解決方案成功發佈到 SharePoint 後,該解決方案將顯示在**解決方案庫中**,您可以在其中啟動它。 有關詳細資訊,請參閱[如何:在遠端伺服器上部署、發佈和升級 SharePoint 解決方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。

### <a name="upgrade-published-packages"></a>升級已發布的套件
 如果在 Visual Studio 中對 SharePoint 專案進行任何更改,則必須升級已發布的包以包括更改。 要成功升級,包必須具有唯一名稱。 如果在 SharePoint 網站上找到具有相同名稱的套件(在更新現有應用程式時可能發生)錯誤會提醒您檔名衝突,並允許您重新命名套件。 重新發佈后,新包將顯示在 SharePoint 網站上,可以升級。 升級的包使用舊包中的數據更新解決方案,然後在 SharePoint 中啟動解決方案。 有關詳細資訊,請參閱[如何:在遠端伺服器上部署、發佈和升級 SharePoint 解決方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。

## <a name="see-also"></a>另請參閱
- [包裝並部署 SharePoint 解決方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
