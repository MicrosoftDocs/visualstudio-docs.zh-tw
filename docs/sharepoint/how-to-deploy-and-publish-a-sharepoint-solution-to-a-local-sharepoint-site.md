---
title: HOW TO：部署並發佈至本機 SharePoint 網站的 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6911c237f5994e809900fcf3bd49e3b9cf83e31c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635224"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>HOW TO：部署並發佈至本機 SharePoint 網站的 SharePoint 方案
  您可以部署或發行至本機 SharePoint 伺服器的 SharePoint 解決方案，在您的開發電腦上。 部署程序副本 *.wsp*檔案至 SharePoint 伺服器，會安裝方案，，，然後啟動功能。 發佈處理只能複製 *.wsp*檔案至 SharePoint 伺服器並將其安裝。 您必須以手動方式啟動它在 SharePoint 中啟用它。

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>若要將 SharePoint 方案部署至本機 SharePoint 伺服器

1.  在 [**方案總管] 中**，選擇您想要部署的專案。

2.  在功能表列上選擇 **建置**，**部署方案**。

     *.Wsp*建立檔並將其安裝在本機 SharePoint 伺服器上。 此外，就會啟動功能。

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>若要將 SharePoint 方案發行至本機 SharePoint 伺服器

1.  在 **方案總管**，開啟您想要發佈，然後選擇 SharePoint 專案的捷徑功能表**發佈**。

2.  在 **發佈**對話方塊方塊中，選擇**發行至檔案系統**選項按鈕。

3.  在 [**目標位置**文字方塊中，輸入本機路徑，然後選擇**發佈**] 按鈕。

     發行進度出現在 Visual Studio**輸出**視窗。 當處理程序完成時，方案 (*.wsp*) 檔案會安裝在本機 SharePoint 伺服器上。 不過，它仍舊需要啟動來在 SharePoint 中。 如果已經存在方案檔，發生錯誤，並詢問您是否要覆寫現有的檔案。 在升級封裝的資訊，請參閱一節，升級中的遠端封裝[How to:部署、 發行和升級 SharePoint 方案，在遠端伺服器上的](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。

## <a name="see-also"></a>另請參閱
- [如何：部署、 發行和升級遠端伺服器上的 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：新增和移除功能和項目加入封裝時，使用封裝設計工具](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
