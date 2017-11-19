---
title: "如何： 部署和發行至本機 SharePoint 網站的 SharePoint 方案 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4959334c9d6949e199ad18934e69ea46e1172b55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站
  您可以部署或發行至本機 SharePoint 伺服器的 SharePoint 方案，在開發電腦上。 部署程序將.wsp 檔案複製到 SharePoint 伺服器、 安裝方案，然後啟動 功能。 在發佈程序只會將.wsp 檔案複製到 SharePoint 伺服器，並將它安裝。 您必須以手動方式啟用它來啟用 SharePoint 中。  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>若要將 SharePoint 方案部署到本機 SharePoint 伺服器  
  
1.  在**方案總管 中**，選擇您想要部署的專案。  
  
2.  在功能表列上選擇 **建置**，**部署方案**。  
  
     建立並在本機 SharePoint 伺服器上安裝.wsp 檔案。 此外，就會啟動功能。  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>若要發行至本機 SharePoint 伺服器的 SharePoint 方案  
  
1.  在**方案總管 中**，開啟您想要發行，然後選擇 SharePoint 專案的捷徑功能表**發行**。  
  
2.  在**發行**對話方塊方塊中，選擇**發行至檔案系統**選項按鈕。  
  
3.  在**目標位置** 文字方塊中，輸入本機路徑，然後選擇**發行** 按鈕。  
  
     發行進度出現在 Visual Studio**輸出**視窗。 處理程序完成時，方案 (.wsp) 檔案被安裝在本機 SharePoint 伺服器上。 不過，它必須仍然啟用，才能在 SharePoint 中使用。 如果方案檔已經存在，就會發生錯誤，並詢問您是否要覆寫現有檔案。 在升級封裝的資訊，請參閱 > 一節，升級中的遠端封裝[如何： 發行，並在遠端伺服器上升級 SharePoint 方案部署](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 部署、 發行和升級遠端伺服器上的 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何： 自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用套件設計工具在套件中新增與移除功能和項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  