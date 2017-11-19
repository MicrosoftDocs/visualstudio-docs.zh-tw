---
title: "如何： 部署、 發行和升級遠端伺服器上的 SharePoint 方案 |Microsoft 文件"
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
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 115509e8ff79aafa703c429b476041d558e3167c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>如何：在遠端伺服器部署、發行和升級 SharePoint 方案
  除了將 SharePoint 方案部署到本機系統，您可以發行至遠端站台或本機 SharePoint 網站的沙箱化 SharePoint 方案。 在遠端發佈程序將.wsp 檔案複製到 SharePoint 伺服器、 安裝方案，然後可讓您啟用方案。 任何變更之後，您也可以升級遠端 SharePoint 方案安裝。  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>若要將沙箱化的 SharePoint 方案發行至遠端 SharePoint 伺服器  
  
1.  在**方案總管] 中**，開啟您想要發行，然後選擇 [沙箱化 SharePoint 專案的捷徑功能表**發行**。  
  
2.  在**發行**對話方塊方塊中，選擇**發行至 SharePoint 網站**選項按鈕，然後再輸入一個線上發行網站，例如以下範例 URL: **https://mytestsite.sharepoint.microsoftonline.com**。  
  
3.  選擇**瀏覽器中開啟方案庫頁面上，在發行後**選項按鈕，檢視中的解決方案清單**解決方案資源庫**發行後的頁面。  
  
4.  選擇**發行** 按鈕。  
  
5.  如果需要使用者驗證，登入遠端伺服器。  
  
     發行進度出現在 Visual Studio**輸出**視窗。 處理程序完成時，遠端 SharePoint 伺服器上安裝方案 (.wsp) 檔案。 不過，您必須仍啟動它才能在 SharePoint 中使用。  
  
6.  在**解決方案資源庫**頁面上選取的 SharePoint 應用程式，然後在功能區中，選擇 [ **Activate** ] 按鈕。  
  
7.  在**啟動方案**對話方塊中的，在功能區中，選擇**Activate**按鈕一次。  
  
     **狀態**上的資料行**解決方案資源庫**頁面會指出應用程式是使用中。  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>若要升級遠端 SharePoint 伺服器上的沙箱化 SharePoint 方案  
 如果遠端伺服器上已發行 SharePoint 沙箱化方案，下列程序可讓您將它升級至應用程式中進行變更之後[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
1.  重新命名中的 SharePoint 封裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要這樣做，請在**方案總管 中**開啟封裝。 它會出現在**封裝總管**。  
  
2.  在**封裝總管**，請在**名稱**方塊中，將封裝名稱變更為唯一的名稱。  
  
3.  儲存專案。  
  
4.  在**方案總管 中**，開啟專案的捷徑功能表，然後選擇**發行**。  
  
5.  在**發行**對話方塊方塊中，選擇**發行至 SharePoint 網站**選項按鈕，並接著，如果方案的儲存位置的遠端伺服器的 URL，輸入。  
  
6.  選擇**瀏覽器中開啟方案庫頁面上，在發行後**選項按鈕，檢視中的解決方案清單**解決方案資源庫**發行後的頁面。  
  
7.  選擇**發行** 按鈕。  
  
8.  如果需要使用者驗證，登入遠端伺服器。  
  
     如果您登入遠端伺服器最近，可能不需要驗證。  
  
     如果具有相同名稱的應用程式的舊版本仍存在 SharePoint 伺服器上，您會收到錯誤，在 SharePoint 伺服器上已經存在相同名稱的封裝。 您必須將封裝重新命名為發行前的唯一名稱。  
  
9. 在 SharePoint 中，選擇新的應用程式，然後在功能區中，選擇**升級** 按鈕。  
  
10. 在**升級方案**對話方塊中的，在功能區中，選擇**升級**按鈕一次。 **狀態**上的資料行**解決方案資源庫**頁面現在應該指出應用程式是使用中。  
  
     停用舊的版本的方案、 新版本的方案，會升級舊的方案，從保留的資料和新的方案會在 SharePoint 中啟動。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 部署和發行至本機 SharePoint 網站的 SharePoint 方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用套件設計工具在套件中新增與移除功能和項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  