---
title: "安全的部署 |Microsoft 文件"
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
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f52c6d26132490defafdf87639e0f1731ea90640
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="secure-deployment"></a>安全的部署
  當您建立 Office 方案時，會自動允許之程式碼執行的專案中更新您的開發電腦。 不過，當您部署方案時，您必須提供的簽署憑證，使用的方案，或使用基礎信任決策的辨識項[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示金鑰。 如需詳細資訊，請參閱[授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 文件層級自訂中，如果您將文件部署到網路位置，您也必須將文件的位置加入信任中心 中的 Office 應用程式的信任位置清單。 如需如何設定終端使用者電腦的文件權限的詳細資訊，請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。  
  
## <a name="preventing-office-solutions-from-running-code"></a>防止 Office 方案執行程式碼  
 系統管理員可以使用登錄以防止所有的 Office 方案的電腦上執行。 具有 managed 程式碼擴充的 Office 方案開啟時，Visual Studio Tools for Office 執行階段檢查的項目是否具有名稱`Disabled`存在電腦上的下列登錄機碼的其中一個下：  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 若要防止 Office 方案執行程式碼，建立`Disabled`之一或兩者的這些登錄機碼下的項目，並指定下列資料類型和值的其中一個`Disabled`:  
  
-   REG_SZ 或 REG_EXPAND_SZ 設為"0"（零） 以外的任何字串中。  
  
-   REG_DWORD 設為 0 （零） 以外的任何值。  
  
 若要啟用 Office 方案執行程式碼，將這兩個`Disabled`項目為 0 （零），或刪除的登錄項目。  
  
## <a name="see-also"></a>請參閱  
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [若要執行或裝載 Office 方案的電腦進行準備工作](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  