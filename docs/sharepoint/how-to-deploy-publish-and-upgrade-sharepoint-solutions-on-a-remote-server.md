---
title: 部署、發佈、& 從遠端升級 SharePoint 方案
titleSuffix: ''
description: 在遠端網站或本機 SharePoint 網站上部署、發行和升級沙箱化 SharePoint 方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ab301f11ffdae03564f05388dfbba55a90d12391
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913682"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>如何：在遠端伺服器上部署、發行和升級 SharePoint 方案
  除了將 SharePoint 方案部署到本機系統之外，您還可以將沙箱化 SharePoint 方案發行至遠端網站或本機 SharePoint 網站。 遠端發佈程式會將 *.wsp* 檔案複製到 SharePoint 伺服器、安裝方案，然後讓您啟用方案。 您也可以在變更遠端 SharePoint 方案後進行升級。

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>將沙箱化 SharePoint 方案發行至遠端 SharePoint 伺服器

1. 在 **方案總管** 中，開啟您要發行之沙箱化 SharePoint 專案的快捷方式功能表，然後選擇 [ **發行**]。

2. 在 [ **發行** ] 對話方塊中，選擇 [ **發行至 SharePoint 網站** ] 選項按鈕，然後輸入線上發行網站的 URL，例如： `https://mytestsite.sharepoint.microsoftonline.com` 。

3. 選擇 [ **發佈之後，在瀏覽器中開啟方案庫] 頁面** ，在發佈之後，于 [ **方案庫** ] 頁面中查看解決方案清單。

4. 選擇 [**發行**] 按鈕。

5. 如果需要使用者驗證，請登入遠端伺服器。

     發佈進度會出現在 Visual Studio 的 **輸出** 視窗中。 當程式完成時，會在遠端 SharePoint 伺服器上安裝 (*.wsp*) 檔案的方案。 不過，它仍然必須先啟用，才能在 SharePoint 中使用。

6. 在 [ **方案庫** ] 頁面上，選取 SharePoint 應用程式，然後在功能區上，選擇 [ **啟用** ] 按鈕。

7. 在 [ **啟用方案** ] 對話方塊的功能區上，再次選擇 [ **啟用** ] 按鈕。

     [**方案庫**] 頁面上的 [**狀態**] 資料行會指出應用程式正在使用中。

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>升級遠端 SharePoint 伺服器上的沙箱化 SharePoint 方案
 如果已在遠端伺服器上發行沙箱化 SharePoint 方案，下列程式可讓您在變更中的應用程式之後進行升級 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

1. 重新命名中的 SharePoint 套件 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 若要這樣做，請在 **方案總管** 開啟封裝。 它會出現在 **套件瀏覽器** 中。

2. 在 [ **封裝瀏覽器**] 的 [ **名稱** ] 方塊中，將封裝名稱變更為唯一的名稱。

3. 儲存專案。

4. 在 **方案總管** 中，開啟專案的快捷方式功能表，然後選擇 [ **發行**]。

5. 在 [ **發行** ] 對話方塊中，選擇 [ **發行至 SharePoint 網站** ] 選項按鈕，然後如果遺漏儲存方案的遠端伺服器的 URL，請輸入該 URL。

6. 選擇 [ **發佈之後，在瀏覽器中開啟方案庫] 頁面** ，在發佈之後，于 [ **方案庫** ] 頁面中查看解決方案清單。

7. 選擇 [**發行**] 按鈕。

8. 如果需要使用者驗證，請登入遠端伺服器。

     如果您最近登入遠端伺服器，則可能不需要驗證。

     如果 SharePoint 伺服器上仍有相同名稱的繼承應用程式，您將會收到一則錯誤，指出 SharePoint 伺服器上已有相同名稱的套件存在。 您必須在發行之前將封裝重新命名為唯一的名稱。

9. 選擇 SharePoint 中的新應用程式，然後在功能區上選擇 [ **升級** ] 按鈕。

10. 在 [ **升級方案** ] 對話方塊的功能區上，再次選擇 [ **升級** ] 按鈕。 [**方案庫**] 頁面上的 [**狀態**] 資料行會指出應用程式正在使用中。

     舊版方案已停用，新版的方案會使用從舊方案維護的資料進行升級，而且新的方案會在 SharePoint 中啟用。

## <a name="see-also"></a>另請參閱
- [如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：使用封裝設計工具加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
