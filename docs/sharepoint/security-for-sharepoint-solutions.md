---
title: SharePoint 方案的安全性 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 982a2387ae0e21304fb9726fabdf05554c982fd5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862938"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含下列功能，可協助強化 SharePoint 應用程式的安全性。

## <a name="safe-control-entries"></a>安全控制項項目
 每個 SharePoint 專案項目中建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]已經**安全控制項項目**表示安全的屬性會控制集合。 其**安全**子屬性可讓您指定您認為安全的控制項。 如需詳細資訊，請參閱 <<c0> [ 提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)並[指定安全的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177521)。

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 屬性
 根據預設，只有完全受信任的執行階段程式碼存取安全性 (CAS) 系統的應用程式可以存取的共用 managed 程式碼組件。 標記具有 AllowPartiallyTrustedCallers 屬性的完全信任組件可讓部分信任組件存取它。

 AllowPartiallyTrustedCallers 屬性加入至任何未部署到系統全域組件快取的 SharePoint 方案 ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 這包括沙箱化方案或方案部署到 SharePoint 應用程式 Bin 目錄。 如需詳細資訊，請參閱 <<c0> [ 適用於 Microsoft.NET Framework 的版本 1 的安全性變更](http://go.microsoft.com/fwlink/?LinkId=177515)並[部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。

## <a name="safe-against-script-property"></a>針對指令碼屬性的安全
 *指令碼資料隱碼攻擊*是各控制項或 Web 網頁上的潛在惡意程式碼插入。 為了協助保護 SharePoint 2010 網站對指令碼資料隱碼攻擊，參與者無法檢視或編輯 預設的 Web 組件或其屬性。 此行為是由稱為 SafeAgainstScript 的 SafeControl 屬性控制。 在  [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將這個屬性設定中的專案項目**安全控制項項目**子屬性**防止指令碼**。 如需詳細資訊，請參閱 <<c0> [ 提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[How to:將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)。

## <a name="vista-and-windows-7-user-account-control"></a>Vista 和 Windows 7 使用者帳戶控制
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]納入做為使用者帳戶控制 (UAC) 的已知的安全性功能。 若要開發 SharePoint 解決方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]並[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系統中，UAC 會要求您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]身為系統管理員。 從**開始**功能表上，開啟捷徑功能表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後選擇**系統管理員身分執行**。

 若要設定[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]捷徑永遠以系統管理員身分執行，開啟其捷徑功能表，選擇**屬性**，選擇 **進階**按鈕**屬性**對話方塊中，然後選取**系統管理員身分執行**核取方塊。

 如需詳細資訊，請參閱 <<c0> [ 了解及 Windows Vista 中設定使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 並[Windows 7 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。

## <a name="sharepoint-permissions-considerations"></a>SharePoint 權限的考量
 若要開發 SharePoint 方案，您必須有足夠的權限來執行和偵錯 SharePoint 方案。 您可以測試 SharePoint 方案之前，請執行下列步驟以確保您擁有必要的權限：

1.  在系統上以系統管理員身分加入您的使用者帳戶。

2.  伺服器陣列系統管理員身分的 SharePoint 伺服器加入您的使用者帳戶。

    1.  在 SharePoint 2010 管理中心內，選擇**管理 farm administrators 群組**連結。

    2.  在  **Farm Administrators**頁面上，選擇**新增**功能表選項

3.  新增您的使用者帳戶至 WSS_ADMIN_WPG 群組。

## <a name="additional-security-resources"></a>其他安全性資源
 如需安全性問題的詳細資訊，請參閱下列文件。

### <a name="visual-studio-security"></a>Visual Studio 安全性

-   [安全性和使用者權限](http://go.microsoft.com/fwlink/?LinkId=177503)

-   [原生和.NET Framework 程式碼中的安全性](http://go.microsoft.com/fwlink/?LinkId=177504)

-   [.NET Framework 中的安全性](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>SharePoint 安全性

-   [SharePoint Foundation 管理和安全性](http://go.microsoft.com/fwlink/?LinkId=177501)

-   [SharePoint 安全性資源中心](http://go.microsoft.com/fwlink/?LinkId=177498)

-   [保護 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177511)

-   [改善 Web 應用程式安全性：威脅與對策](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>一般安全性

-   [MSDN 安全性開發生命週期](http://go.microsoft.com/fwlink/?LinkID=147149)

-   [建置安全的 ASP.NET 應用程式：驗證、 授權和安全通訊](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>另請參閱

- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)