---
title: "如何： 加入專案輸出參考 |Microsoft 文件"
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
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7ced5627420f5ac90da2cae1a2930dbd0b973dbc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-project-output-reference"></a>如何：加入專案輸出參考
  若要部署至 SharePoint 的非 SharePoint 專案的組件 （或 Silverlight 專案中的.xap 檔案），請將其加入做為專案輸出參考。  
  
 此程序會建立兩個專案之間的方案組建相依性。 建置專案輸出參考相關聯的專案之前建置和部署 SharePoint 專案。  
  
### <a name="to-add-a-project-output-reference"></a>若要加入專案輸出參考  
  
1.  載入包含至少一個 SharePoint 專案和一個非 SharePoint 專案的方案。  
  
2.  在**方案總管 中**，選擇 SharePoint 專案節點中的項目。  
  
3.  在**屬性**視窗中，選擇**專案輸出參考**屬性，然後選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP。NET Mobile 設計工具橢圓形")) 旁邊的按鈕。  
  
4.  在**專案輸出參考**對話方塊方塊中，選擇**新增** 按鈕。  
  
5.  在 [屬性] 窗格中，選擇箭號旁**部署類型**屬性，然後選擇適當的值，您所參考，例如非 SharePoint 項目**ElementFile**。  
  
6.  選擇箭號旁**專案名稱**，選擇非 SharePoint 專案項目名稱，然後選擇**確定** 按鈕。  
  
## <a name="see-also"></a>請參閱  
 [提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [如何： 將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  