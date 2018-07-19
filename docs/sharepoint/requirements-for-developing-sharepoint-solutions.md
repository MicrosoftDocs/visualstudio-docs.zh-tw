---
title: 開發 SharePoint 方案的需求 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9d6a726b290bfed1c086f9fb03290a37c91490
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118601"
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>開發 SharePoint 方案的需求
之前您可以使用隨附於 Visual Studio SharePoint 方案的開發工具，您必須在系統上安裝下列必要條件：

- Visual Studio 中使用 C# 和/或 Visual Basic 中或版本的 Visual Studio Application Lifecycle Management (ALM)。

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 安裝在 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

     或

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 安裝在 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位元[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

> [!NOTE]
> 雖然 SharePoint 正式支援只有伺服器作業系統，允許兩個用戶端作業系統：[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]和[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]SP1。 如需詳細資訊，請參閱 < [SharePoint Server 2010 開發人員工作站安裝指南 》](http://go.microsoft.com/fwlink/?LinkID=164557)。

商務資料連接 (BDC) 模型的專案類型需要[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]安裝在系統上。

若要開發 Visual Studio 中的 SharePoint 方案，您必須將 SharePoint 安裝在 Visual Studio 相同的電腦上。 此外，SharePoint 開發人員工具僅支援 SharePoint 獨立組態;不支援伺服陣列 （遠端） 組態。

> [!NOTE]
> Visual Studio 中的 SharePoint 專案只支援[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。 如果您選取[!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)]新的 SharePoint 專案，它將仍為目標[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。

如需有關如何安裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，請參閱 <<c2> [ 安裝 Visual Studio](../install/install-visual-studio.md)。

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista 和 Windows 7 使用者帳戶控制 (UAC)
[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]納入已知為使用者帳戶控制 (UAC) 的安全性功能。 若要開發 SharePoint 解決方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]並[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系統中，UAC 會要求您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]身為系統管理員。 在桌面上，開啟捷徑功能表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後選擇**系統管理員身分執行**。

若要設定為永遠以系統管理員身分執行的桌面捷徑，開啟其捷徑功能表，選擇**屬性**，選擇**進階**按鈕，然後再選取**系統管理員身分執行**核取方塊。

如需詳細資訊，請參閱 <<c0> [ 了解及 Windows Vista 中設定使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 並[Windows 7 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。

## <a name="sharepoint-permissions-considerations"></a>SharePoint 權限的考量
若要開發 SharePoint 方案，您必須有足夠的權限來執行和偵錯 SharePoint 方案。 您可以測試 SharePoint 方案之前，請執行下列步驟以確保您擁有必要的權限：

1. 在系統上以系統管理員身分加入您的使用者帳戶。

2. 伺服器陣列系統管理員身分的 SharePoint 伺服器加入您的使用者帳戶。

    1. 在 SharePoint 管理中心內，選擇**管理 farm administrators 群組**連結。

    2. 在 [ **Farm Administrators**頁面上，選擇**新增**] 按鈕。

3. 新增您的使用者帳戶至 WSS_ADMIN_WPG 群組。

## <a name="see-also"></a>另請參閱
[開始使用&#40;Visual Studio 中的 SharePoint 程式開發&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
