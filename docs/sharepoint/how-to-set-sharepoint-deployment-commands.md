---
title: "如何： 設定 SharePoint 部署命令 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2f465deaaca406c28aab177434e72de9746fb101
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>如何：設定 SharePoint 部署命令
  您可以藉由設定預先部署和部署後命令自訂部署程序。 這些命令之前和之後執行其他部署動作時進行偵錯 SharePoint 方案，從 Visual Studio。  
  
### <a name="to-add-a-pre-deployment-command"></a>若要加入預先部署命令  
  
1.  在功能表列上選擇 **專案**， *ProjectName***屬性**。  
  
2.  選擇**SharePoint**  索引標籤。  
  
3.  在**預先部署命令列**文字方塊中，輸入或 MSBuild 命令，以自訂此步驟。  
  
     例如，若要部署完成之前，請列出目錄內容，輸入**dir**。  
  
### <a name="to-add-a-post-deployment-command"></a>若要加入部署後命令  
  
1.  在功能表列上選擇 **專案**， *ProjectName***屬性**。  
  
2.  選擇**SharePoint**  索引標籤。  
  
3.  在**部署後命令列**文字方塊中，輸入或 MSBuild 命令，以自訂此步驟。  
  
     例如，若要完成部署之後列出目錄內容，輸入**dir**。 若要使用 MSBuild 變數從組建目錄複製組件，請輸入**複製 $ （targetpath) c:\DeploymentDirectory**。  
  
## <a name="see-also"></a>請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  