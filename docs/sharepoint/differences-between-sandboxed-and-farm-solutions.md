---
title: "差異沙箱化方案與伺服器陣列方案 |Microsoft 文件"
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
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d82bc012b2be9736b83fc07f7d0a83d354dda002
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>沙箱化方案與伺服器陣列方案之間的差異
  當您編譯 SharePoint 方案時，將部署至 SharePoint 伺服器，並偵錯工具附加至偵錯。 沙箱化方案屬性的設定取決於用於方案進行偵錯的程序： 沙箱化方案或伺服器陣列方案。  
  
 如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
## <a name="farm-solutions"></a>伺服器陣列方案  
 伺服器陣列方案，其裝載在 IIS 工作者處理序 (W3WP.exe) 中，執行程式碼可能會影響到整部伺服器陣列。 當您偵錯 SharePoint 專案的沙箱化方案屬性設定為 「 伺服器陣列解決方案 」 時，系統的 IIS 應用程式集區回收之前 SharePoint 中撤銷，或部署功能，以釋出鎖定 IIS 工作者處理序的任何檔案。 只有 IIS 應用程式集區處理 SharePoint 專案的網站 URL 就會回收。  
  
## <a name="sandboxed-solutions"></a>沙箱化方案  
 沙箱化方案，其裝載在 SharePoint 使用者程式碼解決方案背景工作處理序 (SPUCWorkerProcess.exe) 中，執行只會影響方案的網站集合的程式碼。 原因是 IIS 背景工作處理序中未執行沙箱化方案，則必須重新啟動 IIS 應用程式集區都 IIS 伺服器。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將偵錯工具附加至 SPUCWorkerProcess 程序，在 SharePoint 中的 SPUserCodeV4 服務都會自動觸發和控制項。 您不需要 SPUCWorkerProcess 處理序回收載入最新版的方案。  
  
## <a name="either-type-of-solution"></a>任一種方案類型  
 使用任一個解決方案類型，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也將偵錯工具附加至瀏覽器以啟用用戶端指令碼偵錯。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用指令碼偵錯引擎會針對此目的。 若要啟用指令碼偵錯，您必須變更預設瀏覽器設定，當系統提示您。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]附加偵錯工具，才能執行目前的站台的 W3WP 或 SPUCWorkerProcess 處理序。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也會將附加 managed COM 加號和工作流程偵錯引擎。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)  
  
  