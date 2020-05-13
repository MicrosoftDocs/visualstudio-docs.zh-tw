---
title: 使用項目工廠建立項目實體微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709055"
---
# <a name="create-project-instances-by-using-project-factories"></a>使用項目工廠建立項目實體
正在使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*專案工廠*創建專案物件的實例的項目類型。 項目工廠類似於可組合 COM 物件的標準類工廠。 但是,專案物件不可預測;因此,專案對象無法創建。它們只能通過使用專案工廠創建。

 當使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入現有專案或在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中 創建新專案時,IDE 調用在 VSPackage 中實現的項目工廠。 新的項目物件為 IDE 提供足夠的資訊來填充**解決方案資源管理員**。 新的項目物件還提供支援IDE啟動的所有相關UI操作所需的介面。

 您可以在專案中的類<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>中實現介面。 通常,它駐留在自己的模組中。

 支援由擁有者聚合的項目必須在其專案檔中保留擁有者密鑰。 當在<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>具有擁有者金鑰的項目上調用該方法時,擁有的專案將其擁有者密鑰轉換為專案工廠 GUID,然後調用此專案`CreateProject`工廠上 的方法執行實際創建。

## <a name="create-an-owned-project"></a>建立擁有的項目
 擁有者分兩個階段建立自有專案:

1. 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>方法。 這使擁有的專案有機會根據輸入控制`IUnknown`創建聚合專案物件。 擁有的專案將內部`IUnknown`物件和聚合物件傳遞回擁有者專案。 這給了擁有的項目一個儲存內部的機會`IUnknown`。

2. 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>方法。 調用此方法時,擁有的專案將執行其所有實例化,而不是`IVsProjectFactory::CreateProject`調用不屬於私有的項目的情況。 輸入`VSOWNEDPROJECTOBJECT`枚舉通常是聚合擁有的專案。 擁有的專案可以使用此變數來確定其專案物件是否已創建(Cookie 不等於 NULL)或必須創建(Cookie 等於 NULL)。

   專案類型由唯一的專案 GUID 識別,類似於可克隆 COM 物件的 CLSID。 通常,一個專案工廠處理創建單個專案類型的實例,儘管可以讓一個專案工廠處理多個專案類型 GUID。

   項目類型與特定的檔名擴展名相關聯。 當使用者嘗試打開現有專案檔或嘗試通過複製樣本建立新專案時,IDE 將使用該檔上的擴充名來確定相應的專案 GUID。

   一旦 IDE 確定是必須創建新項目還是打開特定類型的現有專案,IDE 就會使用 **[HKEY_LOCAL_MACHINE_軟體_Microsoft_VisualStudio_8.0_Project]** 下的系統註冊表中的資訊來查找哪些 VSPackage 實現了所需的專案工廠。 IDE 載入此 VS 套件。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>該方法中,VSPackage 必須通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>調用 方法將其項目工廠註冊到IDE。

   `IVsProjectFactory`介面的主要方法是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>,應處理兩種情況:打開現有專案和創建新專案。 大多數專案將其項目狀態存儲在專案檔中。 通常,通過使範本檔的副本傳遞給`CreateProject`方法,然後打開副本來創建新專案。 通過直接打開傳遞給`CreateProject`方法的專案檔來實例化現有專案。 該方法`CreateProject`可以根據需要向使用者顯示其他 UI 功能。

   專案也可以不使用任何檔,而是將其項目狀態存儲在檔案系統以外的存儲機制中,如資料庫或 Web 伺服器。 在這種情況下,傳遞給`CreateProject`方法的檔名參數實際上不是檔案系統路徑,而是標識項目數據的唯一字串(URL)。 您無需複製傳遞給的範本檔`CreateProject`,以觸發要執行的相應建構序列。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [檢查表:建立新的項目型態](../../extensibility/internals/checklist-creating-new-project-types.md)
