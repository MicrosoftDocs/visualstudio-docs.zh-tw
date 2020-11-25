---
title: 服務對話方塊的進階設定
description: 瞭解如何使用服務功能的 [Advanced Settings] 來設定用戶端應用程式服務的 [advanced settings]。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59ad28dd6890effbac00282a0e9bc388b4191139
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871310"
---
# <a name="advanced-settings-for-services-dialog-box"></a>服務對話方塊的進階設定
用戶端應用程式服務簡化了對 [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] 登入、角色以及 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式的設定檔服務的存取。 您可以使用 [專案設計工具] 的 [服務] 頁面來設定用戶端應用程式服務。 如需 [服務] 頁面的詳細資訊，請參閱[專案設計工具、服務頁](../../ide/reference/services-page-project-designer.md)。

在 [專案設計工具] 中，使用 [服務] 頁面的 [服務的進階設定] 對話方塊，即可設定用戶端應用程式服務的進階設定。 藉由使用這些設定，您可以覆寫一些預設應用程式服務行為，以啟用較少見的案例。 如需詳細資訊，請參閱[用戶端應用程式服務](/dotnet/framework/common-client-technologies/client-application-services)。

若要存取 [服務的進階設定] 對話方塊，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 當 [專案設計工具] 出現時，請按一下 [服務] 索引標籤，然後按一下 [進階] 按鈕。 在您啟用用戶端應用程式服務之前，此按鈕會維持停用狀態。

## <a name="task-list"></a>工作清單

- [如何：設定用戶端應用程式服務](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement 清單

 **在本機儲存密碼雜湊以啟用離線登入** 指定是否將在本機快取加密格式的使用者密碼，以便使用者能在應用程式處於離線模式時登入。 預設會選取這個選項。

 **要求使用者在伺服器 Cookie 過期時必須再次登入** 指定當應用程式存取角色或設定檔服務時，若伺服器驗證 Cookie 已過期，是否會自動重新驗證先前已驗證過的使用者。 選取此選項可拒絕存取應用程式服務，並要求在 Cookie 過期後進行明確重新驗證。 您可以針對部署在公用位置的應用程式，使用這個選項來確保使用應用程式後讓應用程式繼續執行的使用者，不會無限期地保持已驗證的狀態。 依預設，會清除此選項。

 **角色服務快取逾時** 指定用戶端角色提供者將使用已快取的角色值 (而非存取角色服務) 的時間長度。 請在角色經常更新時，將這個時間間隔設定為較小的值，並在角色不常更新時，將其設定為較大的值。 預設值為一天。

當您呼叫 <xref:System.Web.Security.RolePrincipal.IsInRole%2A> 方法時，角色提供者會存取已快取的角色值或角色服務。 若要以程式設計方式清除快取，並強制執行這個方法以存取遠端服務，請呼叫 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> 方法。

 **使用自訂連接字串** 指定用戶端服務提供者是否將使用自訂資料存放區來進行本機快取。 根據預設，服務提供者將使用本機檔案系統來進行快取。 選取此選項將自動以預設連接字串填入文字方塊。 您可以讓預設連接字串繼續自動產生及使用 SQL Server Compact Edition 資料庫，也可以指定現有 SQL Server 資料庫的連接字串。 如需詳細資訊，請參閱 [How to: Configure Client Application Services](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)。 依預設，會清除此選項。

## <a name="see-also"></a>另請參閱

- [用戶端應用程式服務](/dotnet/framework/common-client-technologies/client-application-services)
- [專案設計工具、服務頁](../../ide/reference/services-page-project-designer.md)
- [如何：設定用戶端應用程式服務](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
