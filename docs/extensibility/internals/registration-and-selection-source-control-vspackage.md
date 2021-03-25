---
title: 註冊和選取 (原始檔控制 VSPackage) |Microsoft Docs
description: 瞭解如何使用 Visual Studio 註冊原始檔控制 VSPackage，以及如何從多個已註冊的原始檔控制封裝中選取要載入的封裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ff23784bb833c6a68e368f5db5d3b6f1a7433bb0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069396"
---
# <a name="registration-and-selection-source-control-vspackage"></a>註冊和選取 (原始檔控制 VSPackage)
原始檔控制 VSPackage 必須註冊，才能將它公開至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 如果有一個以上的原始檔控制 VSPackage 註冊，使用者可以選取要在適當時間載入的 VSPackage。 如需 Vspackage 的詳細資訊以及如何註冊的詳細資訊，請參閱 [vspackage](../../extensibility/internals/vspackages.md) 。

## <a name="registering-a-source-control-package"></a>註冊原始檔控制封裝
 原始檔控制封裝會註冊，讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境可以找到它並查詢其支援的功能。 這是根據延遲載入配置，在此配置中，只有在需要或明確要求其功能或命令時，才會建立封裝的實例。

 Vspackage 將資訊放在特定版本的登錄機碼中，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y*，其中 *x* 是主要版本號碼，而 *Y* 是次要版本號碼。 這種做法提供支援多個版本之並存安裝的功能 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者介面 (UI) 可透過原始檔控制介面卡套件) 以及原始檔控制 vspackage，支援從多個已安裝的原始檔控制外掛程式 (中選取專案。 一次只能有一個作用中的原始檔控制外掛程式或 VSPackage。 不過，如以下所述，IDE 允許在原始檔控制外掛程式和 Vspackage 之間，透過自動解決方案型套件交換器制進行切換。 原始檔控制 VSPackage 的部分有一些需求，可啟用此選取機制。

### <a name="registry-entries"></a>登錄項目
 原始檔控制封裝需要三個私用 Guid：

- 套件 GUID：這是封裝的主要 GUID，此封裝包含在本節) 中 ID_Package 的原始檔控制執行 (。

- 原始檔控制 GUID：這是用來向 Visual Studio 原始檔控制存根登錄的原始檔控制 VSPackage 的 GUID，也可以當做命令 UI 內容 GUID 使用。 原始檔控制服務 GUID 會在原始檔控制 GUID 下註冊。 在此範例中，會將原始檔控制 GUID 稱為 ID_SccProvider。

- 原始檔控制服務 GUID：這是本章節) Visual Studio SID_SccPkgService (所使用的私用服務 GUID。 此外，原始檔控制套件必須定義 Vspackage、工具視窗等的其他 Guid。

  下列登錄專案必須由原始檔控制 VSPackage 進行：

| 索引鍵名稱 | 項目 |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` |  (預設) = rg_sz： {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` |  (預設) = rg_sz：\<Friendly name of Package><br /><br /> Service = rg_sz： {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` |  (預設) = rg_sz：#\<Resource ID for localized name><br /><br /> Package = rg_sz： {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br />  (請注意，索引鍵名稱 `SourceCodeControl` 已由使用， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 且無法做為的選項使用 \<PackageName> 。 )  |  (預設) = rg_sz： {ID_Package} |

## <a name="selecting-a-source-control-package"></a>選取原始檔控制封裝
 您可以同時註冊數個原始檔控制外掛程式 API 型外掛程式和原始檔控制 Vspackage。 選取原始檔控制外掛程式或 VSPackage 的程式必須確保 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在適當的時間載入外掛程式或 VSPackage，而且可以延後載入不必要的元件，直到需要它們為止。 此外， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須從其他非使用中的 vspackage （包括功能表項目、對話方塊和工具列）移除所有的 ui，並顯示作用中 VSPackage 的 ui。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 當執行下列任何一項作業時，載入原始檔控制 VSPackage：

- 方案會在方案處於原始檔控制)  (時開啟。

   開啟原始檔控制下的方案或專案時，IDE 會導致載入該方案所指定的原始檔控制 VSPackage。

- 系統會執行原始檔控制 VSPackage 的任何功能表命令。

  原始檔控制 VSPackage 應該只在實際使用時載入所需的任何元件 (亦稱為延遲載入) 。

### <a name="automatic-solution-based-vspackage-swapping"></a>自動以解決方案為基礎的 VSPackage 交換
 您可以透過 [ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **原始檔控制**] 類別下的 [**選項**] 對話方塊，手動交換原始檔控制 vspackage。 自動以方案為基礎的套件交換表示已針對特定方案指定的原始檔控制封裝在開啟該方案時，會自動設為作用中。 每個原始檔控制封裝都應該執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 處理原始檔控制外掛程式 (執行原始檔控制外掛程式 API) 和原始檔控制 Vspackage 之間的切換。

 原始檔控制介面卡封裝可用來切換至任何原始檔控制外掛程式 API 型外掛程式。 切換至中繼原始檔控制介面卡封裝，以及判斷哪些原始檔控制外掛程式必須設定為作用中或非作用中的程式，對使用者而言是透明的。 當任何原始檔控制外掛程式處於作用中狀態時，介面卡套件一律為使用中。 在兩個原始檔控制外掛程式之間切換，只是載入和卸載外掛程式 DLL。 不過，切換至原始檔控制 VSPackage 牽涉到與 IDE 互動以載入適當的 VSPackage。

 當開啟任何方案，而且 VSPackage 的登錄機碼位於方案檔中時，會呼叫原始檔控制 VSPackage。 開啟方案時，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 尋找登錄值並載入適當的原始檔控制 VSPackage。 所有原始檔控制 Vspackage 都必須有上述的登錄專案。 原始檔控制下的方案會標示為與特定的原始檔控制 VSPackage 相關聯。 原始檔控制 Vspackage 必須執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 才能啟用自動以方案為基礎的 VSPackage 交換。

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>適用于封裝選取和切換的 Visual Studio UI
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在 [**原始檔控制**] 類別下的 [**選項**] 對話方塊中，提供原始檔控制 VSPackage 和外掛程式選取的 UI。 它可讓使用者選取作用中的原始檔控制外掛程式或 VSPackage。 下拉式清單包含：

- 所有已安裝的原始檔控制封裝

- 所有已安裝的原始檔控制外掛程式

- 「無」選項，可停用原始程式碼控制

  只會顯示作用中原始檔控制選項的 UI。 VSPackage 選取專案會隱藏上一個 VSPackage 的 UI，並顯示新的 UI。 使用中的 VSPackage 會以每個使用者為基礎來選取。 如果使用者同時開啟多個複本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，每個複本可能會使用不同的使用中 VSPackage。 如果有多個使用者登入同一部電腦，每位使用者都可以開啟個別的實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，每個都有不同的使用中 VSPackage。 當使用者關閉多個實例時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，針對最後一個開啟的方案所使用的原始檔控制 VSPackage 會變成預設的原始檔控制 VSPackage，在重新開機時設為使用中狀態。

  與舊版不同的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是，重新開機 IDE 不再是切換原始檔控制 vspackage 的唯一方法。 VSPackage 選取專案是自動的。 切換封裝需要 Windows 使用者權限 (非系統管理員或 Power 使用者) 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [功能](../../extensibility/internals/source-control-vspackage-features.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
