---
title: 將 SharePoint 方案部署 & 發行至本機 SharePoint 網站
titleSuffix: ''
description: 複習如何將 SharePoint 方案部署或發佈至開發電腦上的本機 SharePoint 伺服器。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 22fe46e2876b14551637dd97712e1728816b020e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913703"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站
  您可以將 SharePoint 方案部署或發佈至開發電腦上的本機 SharePoint 伺服器。 部署程式會將 *.wsp* 檔案複製到 SharePoint 伺服器、安裝方案，然後啟動這些功能。 發佈程式只會將 *.wsp* 檔案複製到 SharePoint 伺服器，並加以安裝。 您必須手動啟用它，才能在 SharePoint 中啟用它。

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>將 SharePoint 方案部署到本機 SharePoint server

1. 在 **方案總管** 中，選擇您想要部署的專案。

2. 在功能表列上，選擇 [ **建立**]、[ **部署方案**]。

     *.Wsp* 檔案會建立並安裝在本機 SharePoint 伺服器上。 此外，也會啟用這些功能。

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>將 SharePoint 方案發行至本機 SharePoint 伺服器

1. 在 **方案總管** 中，開啟您要發行的 SharePoint 專案的快捷方式功能表，然後選擇 [ **發行**]。

2. 在 [ **發行** ] 對話方塊中，選擇 [ **發行至檔案系統** ] 選項按鈕。

3. 在 [ **目標位置** ] 文字方塊中，輸入本機路徑，然後選擇 [ **發行** ] 按鈕。

     發佈進度會出現在 Visual Studio 的 **輸出** 視窗中。 當程式完成時，會在本機 SharePoint 伺服器上安裝 (*.wsp*) 檔案的方案。 不過，它仍然必須啟用才能在 SharePoint 中使用。 如果解決方案檔已存在，就會發生錯誤，並詢問您是否要覆寫現有的檔案。 如需升級封裝的詳細資訊，請參閱 [如何：在遠端伺服器上部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)的升級遠端封裝一節。

## <a name="see-also"></a>另請參閱
- [如何：在遠端伺服器上部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：使用封裝設計工具加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
