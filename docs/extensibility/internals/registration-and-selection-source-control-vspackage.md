---
title: 註冊和選取（原始檔控制 VSPackage） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d6ca60c74ae9956f38418ea6048bb0c8050be2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724512"
---
# <a name="registration-and-selection-source-control-vspackage"></a>註冊和選取 (原始檔控制 VSPackage)
原始檔控制 VSPackage 必須註冊，才能向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 公開。 如果註冊了多個原始檔控制 VSPackage，使用者就可以選取要在適當時間載入哪一個 VSPackage。 如需 Vspackage 的詳細資訊，以及如何註冊這些專案，請參閱[vspackage](../../extensibility/internals/vspackages.md) 。

## <a name="registering-a-source-control-package"></a>註冊原始檔控制封裝
 原始檔控制封裝已註冊，因此 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境可以找到它，並查詢其支援的功能。 這是根據延遲載入配置，其中只有在需要其功能或命令或明確要求時，才會建立封裝的實例。

 Vspackage 會將資訊放在特定版本的登錄機碼中，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*x. y*，其中*X*是主要版本號碼，而*Y*是次要版本號碼。 這種作法可支援多個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的並存安裝。

 @No__t_0 的使用者介面（UI）支援從多個已安裝的原始檔控制外掛程式（透過原始檔控制介面卡套件），以及原始檔控制 Vspackage 的選取專案。 一次只能有一個作用中的原始檔控制外掛程式或 VSPackage。 不過，如下所述，IDE 允許透過自動解決方案式的封裝交換器制，在原始檔控制外掛程式和 Vspackage 之間切換。 原始檔控制 VSPackage 的部分有一些需求，可啟用此選取機制。

### <a name="registry-entries"></a>登錄項目
 原始檔控制套件需要三個私人 Guid：

- 封裝 GUID：這是包含原始檔控制執行之封裝的主要 GUID （在本節中稱為 ID_Package）。

- 原始檔控制 GUID：這是原始檔控制 VSPackage 的 GUID，用來向 Visual Studio 原始檔控制 Stub 註冊，也會當做命令 UI 內容 GUID 使用。 原始檔控制服務 GUID 會在原始檔控制 GUID 之下註冊。 在此範例中，原始檔控制 GUID 稱為 ID_SccProvider。

- 原始檔控制服務 GUID：這是 Visual Studio 所使用的私用服務 GUID （在本節中稱為 SID_SccPkgService）。 此外，原始檔控制封裝也需要定義 Vspackage、工具視窗等的其他 Guid。

  下列登錄專案必須由原始檔控制 VSPackage 所建立：

| 機碼名稱 | 分 |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | （預設值） = rg_sz： {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | （預設值） = rg_sz：封裝 > 的 \<Friendly 名稱<br /><br /> 服務 = rg_sz： {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | （預設值） = rg_sz： # \<Resource > 當地語系化名稱的識別碼<br /><br /> Package = rg_sz： {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> （請注意，索引鍵名稱 `SourceCodeControl` 已由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用，而且無法做為 \<PackageName > 的選擇）。 | （預設值） = rg_sz： {ID_Package} |

## <a name="selecting-a-source-control-package"></a>選取原始檔控制封裝
 數個原始檔控制外掛程式以 API 為基礎的外掛程式和原始檔控制 Vspackage 可能會同時註冊。 選取原始檔控制外掛程式或 VSPackage 的程式必須確定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在適當的時間載入外掛程式或 VSPackage，而且可能會延遲載入不必要的元件，直到需要它們為止。 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須從其他非使用中的 Vspackage 中移除所有 UI，包括功能表項目、對話方塊和工具列，以及顯示作用中 VSPackage 的 UI。

 當執行下列任何一項作業時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入原始檔控制 VSPackage：

- 方案已開啟（當方案在原始檔控制之下時）。

   開啟原始檔控制下的方案或專案時，IDE 會使指定給該方案的原始檔控制 VSPackage 載入。

- [原始檔控制 VSPackage] 的任何功能表命令都會執行。

  原始檔控制 VSPackage 應該只在實際使用時載入其所需的任何元件（亦稱為延遲載入）。

### <a name="automatic-solution-based-vspackage-swapping"></a>自動以解決方案為基礎的 VSPackage 交換
 您可以透過 [**原始檔控制**] 類別下的 [[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**選項**] 對話方塊，手動交換原始檔控制 vspackage。 自動以解決方案為基礎的套件交換表示已針對特定方案指定的原始檔控制封裝，會在該方案開啟時自動設為 [作用中]。 每個原始檔控制封裝都應該執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會處理原始檔控制外掛程式（執行原始檔控制外掛程式 API）和原始檔控制 Vspackage 之間的切換。

 原始檔控制介面卡套件是用來切換至任何原始檔控制外掛程式以 API 為基礎的外掛程式。 切換至中繼原始檔控制介面卡封裝，以及判斷哪些原始檔控制外掛程式必須設定為作用中或非作用中的程式，對使用者而言是透明的。 當任何原始檔控制外掛程式為作用中時，介面卡套件一律是作用中狀態。 在兩個原始檔控制外掛程式之間切換，只是載入和卸載外掛程式 DLL。 不過，切換到原始檔控制 VSPackage 會牽涉到與 IDE 的互動，以載入適當的 VSPackage。

 當開啟任何方案，且 VSPackage 的登錄機碼位於方案檔時，會呼叫原始檔控制 VSPackage。 開啟方案時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會尋找登錄值，並載入適當的原始檔控制 VSPackage。 所有原始檔控制 Vspackage 都必須有上述的登錄專案。 原始檔控制下的方案會標示為與特定的原始檔控制 VSPackage 相關聯。 原始檔控制 Vspackage 必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>，才能啟用自動以解決方案為基礎的 VSPackage 交換。

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>選取和切換套件的 Visual Studio UI
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在 [**原始檔控制**] 類別之下的 [**選項**] 對話方塊中，提供原始檔控制 VSPackage 和外掛程式選擇的 UI。 它允許使用者選取作用中的原始檔控制外掛程式或 VSPackage。 下拉式清單包括：

- 所有已安裝的原始檔控制封裝

- 所有已安裝的原始檔控制外掛程式

- "None" 選項，可停用原始程式碼控制

  只有作用中原始檔控制選項的 UI 是可見的。 VSPackage 選取專案會隱藏先前 VSPackage 的 UI，並顯示新的 ui。 使用中的 VSPackage 會以每個使用者為基礎來選取。 如果使用者有多個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的複本同時開啟，則每一個都可能使用不同的作用中 VSPackage。 如果有多個使用者登入相同的電腦，每個使用者都可以有個別的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 開啟實例，每個都有不同的使用中 VSPackage。 當使用者關閉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的多個實例時，針對最後一個開啟的方案，作用中的原始檔控制 VSPackage 會變成預設的原始檔控制 VSPackage，以在重新開機時設定為使用中狀態。

  不同于舊版的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，IDE 重新開機不再是切換原始檔控制 Vspackage 的唯一方法。 VSPackage 選取專案是自動的。 切換套件需要 Windows 使用者權限（不是系統管理員或 Power User）。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [功能](../../extensibility/internals/source-control-vspackage-features.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage](../../extensibility/internals/vspackages.md)