---
title: SharePoint 解決方案的安全性 |Microsoft Docs
description: 探索 Visual Studio 納入哪些功能，以協助加強 SharePoint 應用程式的安全性。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 588b2af3672851bf7f452287d8383aa2d319347d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881577"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含下列功能，以協助加強 SharePoint 應用程式的安全性。

## <a name="safe-control-entries"></a>安全控制項專案
 在中建立的每個 SharePoint 專案專案 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 都有一個 **安全的控制項** 專案屬性，表示安全的控制項集合。 它的 **安全** 子屬性可讓您指定您認為安全的控制項。 如需詳細資訊，請參閱 [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 和 [指定安全的 Web 組件](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts)。

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 屬性
 依預設，只有由執行時間代碼啟用安全性完全信任的應用程式 (CAS) 系統可以存取共用的 managed 程式碼元件。 使用 AllowPartiallyTrustedCallers 屬性標記完全信任的元件，可讓部分信任的元件存取它。

 AllowPartiallyTrustedCallers 屬性會加入至任何未部署至系統全域組件快取 () 的 SharePoint 方案 [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] 。 這包括沙箱化方案或部署到 SharePoint 應用程式 Bin 目錄的方案。 如需詳細資訊，請參閱 [Microsoft .NET Framework 的第1版安全性變更](/previous-versions/msp-n-p/ff921345(v=pandp.10)) 和 [在 SharePoint Foundation 中部署 Web 組件](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))。

## <a name="safe-against-script-property"></a>安全地針對腳本屬性
 *腳本* 插入會將可能的惡意程式碼插入控制項或網頁中。 為了協助保護 SharePoint 2010 網站免于腳本的插入，參與者預設無法查看或編輯網頁元件或其屬性。 此行為是由稱為 SafeAgainstScript 的 SafeControl 屬性所控制。 在中 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，將專案專案 **安全控制項** 專案子屬性中的這個屬性設定為 **安全的腳本**。 如需詳細資訊，請參閱 [在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 和 [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)。

## <a name="vista-and-windows-7-user-account-control"></a>Vista 和 Windows 7 使用者帳戶控制
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 並 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 將稱為「使用者帳戶控制」的安全性功能 (UAC) 。 若要在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和系統上開發 SharePoint 方案 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] ，UAC 需要您以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 系統管理員身分執行。 在 [ **開始** ] 功能表中，開啟的快捷方式功能表 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，然後選擇 [以 **系統管理員身分執行**]。

 若要將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 快捷方式設定為 [一律以系統管理員身分執行]，請開啟其快捷方式功能表，選擇 [**屬性**]，選擇 [**屬性**] 對話方塊中的 [ **Advanced** ] 按鈕，然後選取 [以 **系統管理員身分執行**] 核取方塊。

 如需詳細資訊，請參閱 [瞭解及設定 Windows Vista 中的使用者帳戶控制](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10))。 和 [Windows 7 使用者帳戶控制](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10))。

## <a name="sharepoint-permissions-considerations"></a>SharePoint 許可權考慮
 若要開發 SharePoint 方案，您必須擁有足夠的許可權來執行和調試 SharePoint 方案。 測試 SharePoint 方案之前，請採取下列步驟以確定您擁有必要的許可權：

1. 將您的使用者帳戶新增為系統的系統管理員。

2. 將您的使用者帳戶新增為 SharePoint 伺服器的伺服器陣列管理員。

    1. 在 SharePoint 2010 管理中心內，選擇 [ **管理伺服器陣列系統管理員群組** ] 連結。

    2. 在 [ **伺服器陣列管理員** ] 頁面上，選擇 [ **新增** ] 功能表選項

3. 將您的使用者帳戶加入至 WSS_ADMIN_WPG 群組。

## <a name="additional-security-resources"></a>其他安全性資源
 如需有關安全性問題的詳細資訊，請參閱下列內容。

### <a name="visual-studio-security"></a>Visual Studio 安全性

- [安全性與使用者權限](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [機器碼和 .NET Framework 程式碼中的安全性](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [.NET Framework 中的安全性](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>SharePoint 安全性

- [SharePoint Foundation 管理和安全性](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [SharePoint 安全性資源中心](/sharepoint/dev/)

- [保護 SharePoint Foundation 中的 Web 組件](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [改進 Web 應用程式安全性：威脅和對策](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>一般安全性

- [MSDN 安全性開發生命週期](https://www.microsoft.com/msrc?rtc=1)

- [建置安全的 ASP.NET 應用程式：驗證、授權和安全通訊](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>另請參閱

- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)