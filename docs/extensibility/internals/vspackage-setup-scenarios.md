---
title: VS包設定方案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703978"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例

設計 VSPackage 安裝程式以獲得靈活性非常重要。 例如,您可能需要在將來發佈安全修補程式,或者可能更改需要全面並行版本控制支援的業務策略。

支援[Visual Studio 的多個版本中](../../extensibility/supporting-multiple-versions-of-visual-studio.md),您可以[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]閱讀有關 透過 VSPackage 的分享或並行安裝支援並行安裝的優勢和問題。 簡而言之,並排 VSPackages 使您能夠最靈活地[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援 的新功能。

本主題中討論的方案不是您唯一的選擇,而是作為建議的最佳做法呈現的。

## <a name="components-privacy-and-sharing"></a>元件、隱私和分享

### <a name="make-your-components-independent"></a>使元件獨立

標識和填充元件、分配和`GUID`部署元件後,無法更改其組合。 如果確實更改了元件的合成,則生成的元件必須是具有新`GUID`的新元件。 鑒於這些事實,通過使每個元件獨立、自力更生的單元,提供了最大的版本控制靈活性。 有關管理元件的規則的詳細資訊,請參閱[更改元件代碼](/windows/desktop/Msi/changing-the-component-code),[以及如果元件規則斷開會發生什麼情況?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>不要將分享資源和私有資源混合在元件中

引用計數發生在元件級別。 因此,將共用和私有資源混合到一個元件中,使得無需覆蓋共用資源即可更新私有資源(如可執行檔)。因此,在一個元件中混合共享資源和私有資源時,無法更新私有資源。 此方案會產生向後相容性問題,並限制您創建並行功能。

例如,用於將 VSPackage 註冊[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]到 的註冊表值應儲存在與用於在 Visual Studio 註冊 VSPackage 的元件分開的元件中。 共用檔或註冊表值進入另一個元件。

## <a name="scenario-1-shared-vspackage"></a>機制機制:分享 VS 套件

在這種情況下,共用 VS 包(支援多個版本的 Visual Studio 的單個二進位檔)在 Windows 安裝程式包中提供。 註冊到每個版本的 Visual Studio 都由用戶可選擇的功能控制。 這也意味著,當分配給單獨的功能時,可以單獨選擇每個元件進行安裝或卸載,從而使用戶能夠控制將 VSPackage 集成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]到 不同版本的 中。 (有關在 Windows 安裝程式套件中使用功能的詳細資訊,請參閱[Windows 安裝程式功能](/windows/desktop/Msi/windows-installer-features)。

![VS 分享 VS 套件安裝程式](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

如圖所示,共用元件是Feat_Common功能的一部分,該功能始終安裝。 通過使Feat_VS2002和Feat_VS2003功能可見,用戶可以在安裝時選擇要將 VSPackage 集成到哪些版本的 Visual Studio。 使用者還可以使用 Windows 安裝程式維護模式添加或刪除功能,在這種情況下,這些功能會從 Visual Studio 的不同版本添加或刪除 VSPackage 註冊資訊。

> [!NOTE]
> 將要素的「顯示」列設置為 0 會隱藏它。 低級別列值(如 1)可確保始終安裝該列。 有關詳細資訊,請參閱[INSTALLLEVEL 屬性](/windows/desktop/Msi/installlevel)和[功能表](/windows/desktop/Msi/feature-table)。

## <a name="scenario-2-shared-vspackage-update"></a>機制 2:分享 VS 套件更新

在這種情況下,方案 1 中的 VSPackage 安裝程式的更新版本已發運。 為了討論,該更新增加了對 Visual Studio 的支援,但它也可以是一個更簡單的安全修補程式或錯誤修復服務包。 Windows 安裝程式安裝較新元件的規則要求不複製系統上已有的未更改元件。 在這種情況下,已有版本 1.0 的系統將覆蓋更新的元件 Comp_MyVSPackage.dll,並允許使用者選擇Feat_VS2005添加新功能及其元件Comp_VS2005_Reg。

> [!CAUTION]
> 每當 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在多個版本之間共用時,VSPackage 的後續版本必須保持與 Visual Studio 的早期版本的向後相容性。 如果無法保持向後相容性,則必須並行使用私有 VSPackages。 有關詳細資訊,請參閱[支援可視化工作室的多個版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

![VS 分享 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

此方案提供了新的 VSPackage 安裝程式,利用 Windows 安裝程式對次要升級的支援。 使用者只需安裝版本 1.1,即可升級版本 1.0。 但是,系統上沒有必要使用版本 1.0。 同一安裝程式將在沒有版本 1.0 的系統上安裝版本 1.1。 以這種方式提供次要升級的優點是,無需完成開發升級安裝程式和完整產品安裝程式的工作。 一個安裝程式執行兩個作業。 安全修補程式或服務包可能會利用 Windows 安裝程式修補程式。 有關詳細資訊,請參閱[修補和升級](/windows/desktop/Msi/patching-and-upgrades)。

## <a name="scenario-3-side-by-side-vspackage"></a>機制 3:並排 VS 套件

此方案提供兩個 VSPackage 安裝程式 - 每個版本的 Visual Studio .NET 2003 和 Visual Studio 一個。 每個安裝程式都安裝並排或私有的 VSPackage(專為特定版本的 Visual Studio 構建和安裝的 VSPackage)。 每個 VS 包都位於其自己的元件中。 因此,每個都可以使用修補程式或維護版本單獨提供服務。 由於 VSPackage DLL 現在特定於版本,因此可以安全地將其註冊資訊包含在與 DLL 相同的元件中。

![VS 並排 VS 套件安裝程式](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

每個安裝程式還包括兩個安裝程式之間共用的代碼。 如果共享程式碼安裝到公共位置,則安裝兩個 .msi 檔將僅安裝一次共用代碼。 第二個安裝程式只是增加元件上的引用計數。 引用計數可確保,如果卸載了其中一個 VS 包,則共用代碼將保留為另一個 VSPackage。 如果卸載第二個 VSPackage,則將刪除共享代碼。

## <a name="scenario-4-side-by-side-vspackage-update"></a>專案 4:並排 VS 套件更新

在這種情況下,適用於 Visual Studio 的 VSPackage 存在安全漏洞,您需要發表更新。 與方案 2 一樣,您可以創建一個新的 .msi 檔案,該檔會更新現有安裝以包括安全修補程式,並在安全修補程式已到位的情況下部署新安裝。

在這種情況下,VSPackage 是安裝在全域程式集緩存 (GAC) 中的託管 VS 包。 重新生成它以包括安全修補程式時,必須更改程式集版本號的修訂號部分。 新程式集版本號的註冊資訊覆蓋以前的版本,從而導致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入固定程式集。

![VS 並排 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

有關並列程式集部署的詳細資訊,請參閱[使用 .NET 框架簡化部署和解決 DLL 地獄](https://msdn.microsoft.com/library/ms973843.aspx)。

## <a name="see-also"></a>另請參閱

- [Windows 安裝程式](/windows/desktop/Msi/windows-installer-portal)
- [支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
