---
title: 差異沙箱化方案與伺服器陣列解決方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967542"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>差異沙箱化方案與伺服器陣列解決方案
  當您編譯 SharePoint 方案時，它會部署到 SharePoint 伺服器，並偵錯工具附加至偵錯。 用於偵錯解決方案的程序取決於沙箱化方案屬性的設定： 沙箱化方案 」 或 「 伺服器陣列方案。

 如需詳細資訊，請參閱 <<c0> [ 沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。

## <a name="farm-solutions"></a>伺服器陣列方案
 伺服器陣列方案，其裝載在 IIS 工作者處理序 (W3WP.exe) 中，執行程式碼，可能會影響整個伺服器陣列。 當您偵錯 SharePoint 專案的沙箱化方案屬性設為 [伺服器陣列方案] 時，系統的 IIS 應用程式集區回收之前 SharePoint 撤銷，或部署的功能，以釋放任何由 IIS 工作者處理序鎖定的檔案。 只有 IIS 應用程式集區提供 SharePoint 專案的網站 URL 就會回收。

## <a name="sandboxed-solutions"></a>沙箱化方案
 沙箱化方案，其裝載在 SharePoint 使用者程式碼方案背景工作處理序 (SPUCWorkerProcess.exe) 中，執行程式碼，只會影響方案的網站集合。 原因是 IIS 工作者處理序中未執行沙箱化方案，則必須重新啟動 IIS 應用程式集區和 IIS 伺服器都不。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將偵錯工具附加至 SPUCWorkerProcess SPUserCodeV4 服務在 SharePoint 中的自動觸發程序的程序和控制項。 您不需要 SPUCWorkerProcess 處理序回收載入解決方案的最新版本。

## <a name="either-type-of-solution"></a>任一種類型的解決方案
 其中一個解決方案類型，與[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也將偵錯工具附加至瀏覽器，以啟用用戶端指令碼偵錯。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用指令碼偵錯引擎，針對此目的。 若要啟用指令碼偵錯，您必須變更預設瀏覽器設定，當系統提示您。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 附加偵錯工具，才能執行目前的站台的 W3WP 或 SPUCWorkerProcess 程序。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 也會將附加的受管理的 COM Plus 和工作流程偵錯引擎。

## <a name="see-also"></a>另請參閱
- [偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)
