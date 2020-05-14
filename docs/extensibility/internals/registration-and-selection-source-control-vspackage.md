---
title: 註冊和選擇(源控制 VS 包) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705712"
---
# <a name="registration-and-selection-source-control-vspackage"></a>註冊和選取 (原始檔控制 VSPackage)
必須註冊原始碼管理 VSPackage 才能將[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]公開給 。 如果註冊了多個原始程式碼管理 VSPackage,用戶可以選擇在適當時間載入的 VSPackage。 有關[VSPackages](../../extensibility/internals/vspackages.md)以及如何註冊它們的更多詳細資訊,請參閱 VS 包。

## <a name="registering-a-source-control-package"></a>註冊原始碼管理員
 源控件包已註冊,以便[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境可以找到它並查詢其支援的功能。 這符合延遲載入方案,其中僅在需要或顯式請求包的功能或命令時創建包實例。

 VS包將資訊放在特定於版本的註冊表項中\\,HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio*X.Y,* 其中*X*是主要版本號 *,Y*是次要版本號。 這種做法提供了支援並行安裝多個版本的的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能。

 使用者介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](UI) 支援從多個已安裝的原始程式碼管理外掛程式(透過原始碼管理配接器套件)和原始程式碼管理 VSPackage 中進行選擇。 一次只能有一個活動原始程式碼管理外掛程式或 VSPackage。 但是,如下所述,IDE 允許透過基於解決方案的自動包交換機制在原始程式碼管理外掛程式和 VSPackage 之間切換。 原始碼管理 VSPackage 有一些要求來啟用此選擇機制。

### <a name="registry-entries"></a>登錄項目
 原始碼管理套件需要三個專用 GUID:

- 包 GUID:這是包含原始程式碼管理實現(本節中稱為ID_Package)的包的主要 GUID。

- 原始程式碼管理 GUID:這是用於向可視化工作室原始碼管理存根註冊的原始程式碼管理 VSPackage 的 GUID,也可用作命令 UI 上下文 GUID。 原始程式碼管理服務 GUID 在原始碼管理 GUID 下註冊。 在此示例中,源控件 GUID 稱為ID_SccProvider。

- 原始程式碼管理服務 GUID:這是 Visual Studio 使用的專用服務 GUID(本節中稱為SID_SccPkgService)。 除此之外,原始程式碼管理包還需要為 VSPackage、工具視窗等定義其他 GUID。

  以下註冊表項必須由原始碼管理 VSPackage 進行:

| 機碼名稱 | 項目 |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (默認) = rg_sz:[ID_SccProvider] |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (預設)\<= rg_sz:包>的友好名稱<br /><br /> 服務 = rg_sz:[SID_SccPkgService] |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (預設) = rg_sz:*\<本地化名稱的資源 ID><br /><br /> 包 = rg_sz:[ID_Package] |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (請注意,金鑰名稱`SourceCodeControl`、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已由 和\<不可用作為 包名稱>的選擇。 | (默認) = rg_sz:[ID_Package] |

## <a name="selecting-a-source-control-package"></a>選擇原始碼管理員
 可以同時註冊多個基於原始程式碼管理外掛程式的外掛程式和原始程式碼管理 VS 包。 選擇原始程式碼管理外掛程式或 VSPackage 的過程必須[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]確保在適當的時間 載入外掛程式或 VSPackage,並可以延遲載入不必要的元件,直到需要它們。 此外,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須從其他非活動 VS 包中刪除所有 UI,包括選單項、對話框和工具列,並顯示活動 VSPackage 的 UI。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]執行以下任一動作時,載入原始碼管理 VSPackage:

- 解決方案打開(當解決方案處於原始程式碼控制之下時)。

   打開原始碼管理下的解決方案或專案時,IDE會導致載入為該解決方案指定的原始程式碼管理 VSPackage。

- 將執行原始碼管理 VSPackage 的任何功能表命令。

  原始碼管理 VSPackage 應僅在實際使用元件(也稱為延遲載入)時載入其所需的任何元件。

### <a name="automatic-solution-based-vspackage-swapping"></a>基於解決方案的自動 VS 套件交換
 您可以透過 **「源控制**」[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]類別下的 **「選項**」對話方塊手動交換原始碼管理 VS 套件。 基於解決方案的自動包交換意味著在打開該解決方案時,已為特定解決方案指定的原始程式碼管理包將自動設置為活動。 每個原始碼管理員都應實<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>作與 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處理原始碼管理外掛程式(實現原始碼管理外掛程式 API)和原始程式碼管理 VS 套件之間的交換機。

 原始碼管理介面管理介面管理外掛程式的外掛程式 API。 切換到中間原始程式碼管理配接器包並確定必須設置為活動或非活動的原始程式碼管理外掛程式的過程對使用者是透明的。 當任何原始程式碼管理外掛程式處於活動狀態時,適配器包始終處於活動狀態。 在兩個原始程式碼管理外掛程式之間切換只需載入和卸載外掛程式 DLL 即可。 但是,切換到原始程式碼管理 VSPackage 需要與 IDE 互動以載入相應的 VSPackage。

 當打開任何解決方案並且 VSPackage 的註冊表項位於解決方案檔中時,將調用原始程式碼管理 VSPackage。 打開解決方案後,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]尋找註冊表值並載入相應的原始程式碼管理 VSPackage。 所有原始碼管理 VS 包必須具有上述註冊表項。 受原始碼管理的解決方案被標記為與特定的原始碼管理 VSPackage 相關聯。 原始碼管理 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>必須實現實現,以啟用基於解決方案的自動 VSPackage 交換。

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>用來選擇與切換的視覺化工作室 UI
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在 **「源控制**」類別下的 **「選項**」對話框中為源代碼管理 VSPackage 和外掛程式選擇提供 UI。 它允許使用者選擇活動源控制外掛程式或 VSPackage。 下拉清單包括:

- 所有已安裝的源碼管理套件

- 所有已安裝的源碼管理外掛程式

- 關閉原始碼控制的「無」選項

  只有活動原始程式碼管理選擇的 UI 可見。 VSPackage 選擇隱藏上一個 VSPackage 的 UI,並顯示新 VSPackage 的 UI。 活動 VS 包是按使用者選擇的。 如果使用者具有多個同時打開的副本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],則每個副本可能使用不同的活動 VS 包。 如果多個使用者登錄到同一台電腦,則每個使用者可以具有單獨的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]打開實例,每個實例具有不同的活動 VSPackage。 當使用者關閉的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]多個實例時,為最後一個打開的解決方案處於活動狀態的原始程式碼管理 VSPackage 將成為預設原始程式碼管理 VSPackage,在重新啟動時設置為活動。

  與的早期版本不同[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],IDE 重新啟動不再是切換原始程式碼管理 VSPackages 的唯一方法。 VSPackage 選擇是自動的。 切換包需要 Windows 用戶許可權(不是管理員或超級使用者)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [特性](../../extensibility/internals/source-control-vspackage-features.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage](../../extensibility/internals/vspackages.md)
