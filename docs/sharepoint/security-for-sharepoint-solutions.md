---
title: "SharePoint 方案的安全性 |Microsoft 文件"
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
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6e9aff74a49f738f4a0ed0df68ffe2e9a5b33525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]加入了下列功能，可協助強化 SharePoint 應用程式的安全性。  
  
## <a name="safe-control-entries"></a>安全控制項項目  
 每個 SharePoint 專案項目中建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有**安全控制項項目**屬性代表安全控制項集合。 其**安全**子屬性可讓您指定您認為安全的控制項。 如需詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[指定安全的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177521)。  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 屬性  
 根據預設，只有完全受執行階段程式碼存取安全性 (CAS) 系統的應用程式可以存取的共用 managed 程式碼組件。 標記使用 AllowPartiallyTrustedCallers 屬性的完全信任組件可讓部分信任組件存取它。  
  
 AllowPartiallyTrustedCallers 屬性會加入至系統全域組件快取未部署任何 SharePoint 方案 ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 這包括沙箱化方案或方案部署到 SharePoint 應用程式 Bin 目錄。 如需詳細資訊，請參閱[適用於 Microsoft.NET Framework 版本 1 的安全性變更](http://go.microsoft.com/fwlink/?LinkId=177515)和[部署在 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
## <a name="safe-against-script-property"></a>針對指令碼屬性的安全  
 *指令碼資料隱碼*是控制項或網頁上的潛在惡意程式碼插入。 若要保護 SharePoint 2010 網站針對指令碼資料隱碼，參與者無法檢視或編輯預設 Web 組件或其屬性。 此行為是由稱為 SafeAgainstScript 的 SafeControl 屬性控制。 在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，將此屬性中的專案項目**安全控制項項目**子屬性**防止指令碼**。 如需詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[如何： 為安全控制項的標記控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)。  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista 和 Windows 7 的使用者帳戶控制  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]納入做為使用者帳戶控制 (UAC) 的已知的安全性功能。 若要開發 SharePoint 方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系統，UAC 會要求您執行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]身為系統管理員。 從**啟動**功能表上，開啟捷徑功能表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後選擇 **系統管理員身分執行**。  
  
 若要設定[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]捷徑永遠以系統管理員身分執行，開啟其捷徑功能表，選擇**屬性**，選擇**進階**按鈕**屬性**對話方塊，然後選取**系統管理員身分執行**核取方塊。  
  
 如需詳細資訊，請參閱[了解與 Windows Vista 中設定使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 和[7 的 Windows 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## <a name="sharepoint-permissions-considerations"></a>SharePoint 權限的考量  
 若要開發 SharePoint 方案，您必須執行和偵錯 SharePoint 方案的足夠權限。 您可以測試 SharePoint 方案之前，請採取下列步驟，請確定您有必要的權限：  
  
1.  將您的使用者帳戶新增為系統上的系統管理員。  
  
2.  將您的使用者帳戶加入 SharePoint 伺服器做為伺服器陣列管理員。  
  
    1.  在 SharePoint 2010 管理中心 中選擇**管理伺服器陣列管理員群組**連結。  
  
    2.  在**伺服陣列管理員**頁面上，選擇**新增**功能表選項  
  
3.  新增您的使用者帳戶到 WSS_ADMIN_WPG 群組。  
  
## <a name="additional-security-resources"></a>其他安全性資源  
 如需安全性問題的詳細資訊，請參閱下列文件。  
  
### <a name="visual-studio-security"></a>Visual Studio 安全性  
  
-   [安全性和使用者權限](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [原生和.NET Framework 程式碼中的安全性](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [在.NET Framework 安全性](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>SharePoint 安全性  
  
-   [SharePoint Foundation 系統管理和安全性](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint 安全資源中心](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [保護 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [改善 Web 應用程式的安全性： 威脅與因應對策](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>一般安全性  
  
-   [MSDN 安全性開發生命週期](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [建立安全的 ASP.NET 應用程式： 驗證、 授權和安全通訊](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  