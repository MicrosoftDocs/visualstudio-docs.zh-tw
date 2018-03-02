---
title: "開發 SharePoint 方案的需求 |Microsoft 文件"
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
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4591bef62d9e3d639e6dfca44c0b2625a8e02de5
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>開發 SharePoint 方案的要求
 
之前，您可以使用 Visual Studio 中包含的 SharePoint 方案開發工具，您必須在系統上安裝下列先決條件：

- Visual Studio 中使用 C# 和/或 Visual Basic 中或版本的 Visual Studio Application Lifecycle Management (ALM)。

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 安裝在 64 位元上[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

     或

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 安裝在 64 位元上[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

> [!NOTE]
> 而只有伺服器作業系統的正式支援 SharePoint 所，允許兩個用戶端作業系統：[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]和[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]SP1。 如需詳細資訊，請參閱[SharePoint Server 2010 開發人員工作站安裝指南 》](http://go.microsoft.com/fwlink/?LinkID=164557)。

商務資料連線 (BDC) 模型專案類型需要[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]系統上安裝。

若要開發 Visual Studio 中的 SharePoint 方案，您必須在 Visual Studio 的同一部機器上安裝 SharePoint。 此外，SharePoint 開發人員工具僅支援 SharePoint 獨立組態。不支援伺服陣列 （遠端） 組態。

> [!NOTE]
> Visual Studio 中的 SharePoint 專案僅支援[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。 如果您選取[!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)]對於新的 SharePoint 專案，它將仍為目標[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。

如需有關如何安裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，請參閱[安裝 Visual Studio](../install/install-visual-studio.md)。

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista 和 Windows 7 使用者帳戶控制 (UAC)

[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]納入已知為使用者帳戶控制 (UAC) 的安全性功能。 若要開發 SharePoint 方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系統，UAC 會要求您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]身為系統管理員。 在桌面上，開啟捷徑功能表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後選擇 **系統管理員身分執行**。

若要設定為永遠以系統管理員身分執行的桌面捷徑，開啟其捷徑功能表，選擇 **屬性**，選擇**進階**按鈕，然後再選取**系統管理員身分執行**核取方塊。

如需詳細資訊，請參閱[了解與 Windows Vista 中設定使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 和[7 的 Windows 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。

## <a name="sharepoint-permissions-considerations"></a>SharePoint 權限的考量

若要開發 SharePoint 方案，您必須執行和偵錯 SharePoint 方案的足夠權限。 您可以測試 SharePoint 方案之前，請採取下列步驟，請確定您有必要的權限：

1. 將您的使用者帳戶新增為系統上的系統管理員。

2. 將您的使用者帳戶加入 SharePoint 伺服器做為伺服器陣列管理員。

    1. 在 SharePoint 管理中心內，選擇 **管理伺服器陣列管理員群組**連結。

    2. 在**伺服陣列管理員**頁面上，選擇**新增** 按鈕。

3. 新增您的使用者帳戶到 WSS_ADMIN_WPG 群組。

## <a name="see-also"></a>請參閱

[開始使用 &#40;Visual Studio &#41; 中的 SharePoint 開發](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)