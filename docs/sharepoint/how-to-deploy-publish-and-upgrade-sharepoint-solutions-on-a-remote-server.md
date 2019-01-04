---
title: HOW TO：部署、 發行和升級遠端伺服器上的 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1473d1c9ea9d876eb539e9672c1675ce06d9762d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835668"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>HOW TO：部署、 發行和升級遠端伺服器上的 SharePoint 方案
  除了本機系統中部署 SharePoint 方案，您可以在遠端站台或本機 SharePoint 網站發行沙箱化 SharePoint 方案。 遠端發行的程序副本 *.wsp*檔案至 SharePoint 伺服器，安裝方案，並接著可讓您啟用此解決方案。 對它進行變更之後，您也可以升級遠端 SharePoint 方案安裝。  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>若要將沙箱化 SharePoint 方案發行至遠端 SharePoint 伺服器  
  
1.  在 **方案總管**，開啟您想要發佈，然後選擇 沙箱化 SharePoint 專案的捷徑功能表**發佈**。  
  
2.  在 **發佈**對話方塊方塊中，選擇**發行至 SharePoint 網站**選項按鈕，然後再輸入 URL online 發行網站，例如： `https://mytestsite.sharepoint.microsoftonline.com`。  
  
3.  選擇**瀏覽器中開啟 [解決方案資源庫] 頁面，在發行後**選項按鈕，檢視中的解決方案清單**解決方案資源庫**發行後的頁面。  
  
4.  選擇**發佈** 按鈕。  
  
5.  如果需要使用者驗證，登入遠端伺服器。  
  
     發行進度出現在 Visual Studio**輸出**視窗。 當處理程序完成時，方案 (*.wsp*) 檔案會安裝遠端 SharePoint 伺服器上。 不過，它仍舊需要啟動才可以在 SharePoint 中使用。  
  
6.  在 **解決方案資源庫**頁面上選取的 SharePoint 應用程式，然後在功能區中，選擇  **Activate**  按鈕。  
  
7.  在**啟用的解決方案** 對話方塊中，於功能區中，選擇**Activate**按鈕一次。  
  
     **狀態**上的資料行**解決方案資源庫**頁面會指出應用程式使用中。  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>若要升級遠端 SharePoint 伺服器上的沙箱化 SharePoint 方案  
 如果遠端伺服器上已沙箱化 SharePoint 方案，下列程序可讓您在變更中的應用程式之後將它升級[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
1.  重新命名在 SharePoint 封裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要這樣做，請在**方案總管 中**開啟封裝。 它會出現在**套件總管**。  
  
2.  在 **套件總管**，請在**名稱**方塊中，將封裝名稱變更為唯一的名稱。  
  
3.  儲存專案。  
  
4.  在 **方案總管**，開啟專案的捷徑功能表，然後選擇**發佈**。  
  
5.  在 **發佈**對話方塊方塊中，選擇**發行至 SharePoint 網站**選項按鈕，並接著，如果解決方案中的儲存位置的遠端伺服器的 URL，輸入。  
  
6.  選擇**瀏覽器中開啟 [解決方案資源庫] 頁面，在發行後**選項按鈕，檢視中的解決方案清單**解決方案資源庫**發行後的頁面。  
  
7.  選擇**發佈** 按鈕。  
  
8.  如果需要使用者驗證，登入遠端伺服器。  
  
     如果您登入遠端伺服器最近，可能不需要驗證。  
  
     如果具有相同名稱的應用程式的舊版仍然存在 SharePoint 伺服器上，您會收到錯誤，在 SharePoint 伺服器上已經存在具有相同名稱的封裝。 您必須將封裝重新命名為發行前的唯一名稱。  
  
9. 在 SharePoint 中，選擇新的應用程式，然後在功能區中，選擇**升級** 按鈕。  
  
10. 在 [**升級方案**] 對話方塊中，於功能區中，選擇**升級**按鈕一次。 **狀態**上的資料行**解決方案資源庫**頁面上現在應該指出應用程式是使用中。  
  
     停用舊版本的解決方案，解決方案的新版本升級舊的解決方案，從保留的資料並在 SharePoint 中啟動新的方案。  
  
## <a name="see-also"></a>另請參閱
 [如何：部署並發佈至本機 SharePoint 網站的 SharePoint 方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：新增和移除功能和項目加入封裝時，使用封裝設計工具](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
