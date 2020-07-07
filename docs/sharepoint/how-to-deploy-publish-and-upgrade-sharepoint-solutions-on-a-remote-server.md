---
title: 部署、發佈、& 從遠端升級 SharePoint 方案
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f05f42f8aed35696b962e71a5fce86c2956b3661
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016811"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>如何：在遠端伺服器上部署、發行和升級 SharePoint 方案
  除了將 SharePoint 方案部署到本機系統以外，您還可以將沙箱化 SharePoint 方案發行到遠端網站或本機 SharePoint 網站。 遠端發佈程式會將 *.wsp*檔案複製到 SharePoint 伺服器、安裝方案，然後讓您啟用方案。 您也可以在進行變更之後，升級遠端 SharePoint 方案安裝。

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>將沙箱化 SharePoint 方案發行至遠端 SharePoint 伺服器

1. 在**方案總管**中，開啟您要發行之沙箱化 SharePoint 專案的快捷方式功能表，然後選擇 [**發行**]。

2. 在 [**發行**] 對話方塊中，選擇 [**發行至 SharePoint 網站**] 選項按鈕，然後輸入線上發佈網站的 URL，例如： `https://mytestsite.sharepoint.microsoftonline.com` 。

3. 選擇 [**發佈之後，在瀏覽器中開啟方案庫**] 選項按鈕，以在發行後查看 [**方案庫**] 頁面中的方案清單。

4. 選擇 [**發行**] 按鈕。

5. 如果需要使用者驗證，請登入遠端伺服器。

     發行進度會出現在 Visual Studio 的 [**輸出**] 視窗中。 當程式完成時，會在遠端 SharePoint 伺服器上安裝方案（*.wsp*）檔案。 不過，它仍然必須先啟用，才能在 SharePoint 中使用。

6. 在 [**方案庫**] 頁面上，選取 SharePoint 應用程式，然後在功能區上選擇 [**啟動**] 按鈕。

7. 在 [**啟用方案**] 對話方塊的功能區上，再次選擇 [**啟動**] 按鈕。

     [**方案庫**] 頁面上的 [**狀態**] 資料行會指出應用程式正在使用中。

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>升級遠端 SharePoint 伺服器上的沙箱化 SharePoint 方案
 如果沙箱化 SharePoint 方案已經在遠端伺服器上發行，下列程式可讓您在對中的應用程式進行變更之後，將它升級 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

1. 在中重新命名 SharePoint 封裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 若要這麼做，請在**方案總管**開啟封裝。 它會出現在 [**封裝瀏覽器**] 中。

2. 在 [ **Package Explorer**] 的 [**名稱**] 方塊中，將封裝名稱變更為唯一的名稱。

3. 儲存專案。

4. 在**方案總管**中，開啟專案的快捷方式功能表，然後選擇 [**發行**]。

5. 在 [**發行**] 對話方塊中，選擇 [**發行至 SharePoint 網站**] 選項按鈕，然後如果遺漏儲存解決方案的遠端伺服器 URL，請輸入它。

6. 選擇 [**發佈之後，在瀏覽器中開啟方案庫**] 選項按鈕，以在發行後查看 [**方案庫**] 頁面中的方案清單。

7. 選擇 [**發行**] 按鈕。

8. 如果需要使用者驗證，請登入遠端伺服器。

     如果您最近登入遠端伺服器，可能就不需要進行驗證。

     如果 SharePoint 伺服器上仍有相同名稱的繼承應用程式，您會收到一則錯誤，指出 SharePoint 伺服器上已有相同名稱的套件。 發行之前，您必須先將封裝重新命名為唯一名稱。

9. 選擇 SharePoint 中的新應用程式，然後在功能區上選擇 [**升級**] 按鈕。

10. 在 [**升級方案**] 對話方塊的功能區上，再次選擇 [**升級**] 按鈕。 [**方案庫**] 頁面上的 [**狀態**] 欄位現在應該會指出應用程式為使用中狀態。

     舊版的解決方案會停用，新版本的解決方案會使用從舊解決方案維護的資料進行升級，而新的方案則會在 SharePoint 中啟用。

## <a name="see-also"></a>另請參閱
- [如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：使用封裝設計工具在封裝中加入和移除功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
