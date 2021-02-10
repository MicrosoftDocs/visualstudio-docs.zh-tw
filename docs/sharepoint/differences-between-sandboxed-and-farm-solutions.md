---
title: 沙箱化與伺服器陣列方案之間的差異 |Microsoft Docs
description: 瞭解沙箱化與伺服器陣列方案之間的差異。 瞭解 Visual Studio 如何使用任一種類型的解決方案進行調試。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cea66f313a8c6c8ad7fc390a3ca126d92139725c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948774"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>沙箱化與伺服器陣列方案之間的差異
  當您編譯 SharePoint 方案時，它會部署到 SharePoint 伺服器，而偵錯工具會附加至偵錯工具。 用來偵測解決方案的程式取決於沙箱化方案屬性的設定：沙箱化方案或伺服器陣列方案。

 如需詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

## <a name="farm-solutions"></a>伺服器陣列方案
 伺服器陣列方案（裝載于 IIS 背景工作進程 ( # A0) ）會執行可能影響整個伺服器陣列的程式碼。 當您將沙箱化方案屬性設為「伺服器陣列方案」的 SharePoint 專案進行偵錯工具時，系統的 IIS 應用程式集區會在 SharePoint 撤銷或部署功能之前回收，以便釋放 IIS 背景工作進程所鎖定的任何檔案。 只有提供 SharePoint 專案網站 URL 的 IIS 應用程式集區會被回收。

## <a name="sandboxed-solutions"></a>沙箱化解決方案
 沙箱化方案（裝載于 SharePoint 使用者程式碼解決方案工作者進程 ( # A0) 中）執行的程式碼只會影響解決方案的網站集合。 由於沙箱化方案無法在 IIS 背景工作進程中執行，IIS 應用程式集區或 IIS 伺服器都不需要重新開機。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將偵錯工具附加至 Spucworkerprocess.exe 進程，而 SharePoint 中的 SPUserCodeV4 服務會自動觸發和控制項。 Spucworkerprocess.exe 程式不需要回收以載入最新版本的解決方案。

## <a name="either-type-of-solution"></a>任一類型的解決方案
 使用任一種解決方案類型時，也會將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具附加至瀏覽器，以啟用用戶端腳本的偵錯工具。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用腳本偵測引擎進行此用途。 若要啟用腳本偵測，您必須在系統提示時變更預設瀏覽器設定。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只會將偵錯工具附加至執行目前網站的 W3WP.EXE 或 Spucworkerprocess.exe 進程。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 也附加 managed COM Plus 和工作流程調試引擎。

## <a name="see-also"></a>另請參閱
- [調試 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)
