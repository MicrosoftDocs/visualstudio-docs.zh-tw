---
title: VSPackage 安裝案例 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eddfc0aa9b8f5b3a169ce87b31a2221983f57aaa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722177"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例

請務必設計您的 VSPackage 安裝程式以提供彈性。 例如，您可能需要在未來釋放安全性修補程式，或者您可能會變更需要全面並存版本控制支援的商務策略。

在[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)中，您可以閱讀使用 VSPackage 的共用或並存安裝，來支援 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 並存安裝的優點和問題。 簡言之，並存 Vspackage 提供您最大的彈性來支援 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的新功能。

本主題所討論的案例並不是您唯一的選擇，但會顯示為建議的最佳作法。

## <a name="components-privacy-and-sharing"></a>元件、隱私權和共用

### <a name="make-your-components-independent"></a>使元件獨立

一旦您識別並填入元件、指派 `GUID`，並部署元件，就無法變更其組合。 如果您變更了元件的組合，則產生的元件必須是具有新 `GUID` 的新元件。 基於這些事實，藉由讓每個元件各自獨立的單位，可提供最大的版本控制彈性。 如需有關管理元件之規則的詳細資訊，請參閱[變更元件程式碼](/windows/desktop/Msi/changing-the-component-code)和[如果元件規則中斷會發生什麼情況？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>不要在元件中混用共用和私人資源

參考計數發生在元件層級上。 因此，在一個元件中混用共用和私人資源，可讓您無法更新私用資源（例如可執行檔），也不會覆寫共用資源。 此案例會建立回溯相容性問題，並限制您無法建立並存功能。

例如，用來向 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 註冊 VSPackage 的登錄值應該保存在與用來向 Visual Studio 註冊您的 VSPackage 不同的元件中。 共用檔案或登錄值還會移到另一個元件中。

## <a name="scenario-1-shared-vspackage"></a>案例1：共用 VSPackage

在此案例中，共用 VSPackage （支援多個版本 Visual Studio 的單一二進位檔會隨附于 Windows Installer 套件中。 向每個版本的 Visual Studio 註冊，都是由使用者可選取的功能所控制。 這也表示指派給個別功能時，可以個別選取每個元件進行安裝或卸載，讓使用者控制將 VSPackage 整合到不同版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 （如需使用 Windows Installer 套件中功能的詳細資訊，請參閱[Windows Installer 功能](/windows/desktop/Msi/windows-installer-features)）。

![VS Shared VSPackage 安裝程式](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

如圖所示，共用元件會成為 Feat_Common 功能的一部分，這是一律會安裝的部分。 藉由讓 Feat_VS2002 和 Feat_VS2003 功能可見，使用者可以在安裝時選擇要讓 VSPackage 整合的 Visual Studio 版本。 使用者也可以使用 Windows Installer 維護模式來新增或移除功能，在此情況下，會在不同版本的 Visual Studio 中新增或移除 VSPackage 註冊資訊。

> [!NOTE]
> 將功能的 [顯示] 資料行設定為0會將它隱藏。 低層級的資料行值（例如1）可確保一律會安裝。 如需詳細資訊，請參閱[INSTALLLEVEL 屬性](/windows/desktop/Msi/installlevel)和[功能資料表](/windows/desktop/Msi/feature-table)。

## <a name="scenario-2-shared-vspackage-update"></a>案例2：共用 VSPackage 更新

在此案例中，會隨附案例1中的 VSPackage 安裝程式更新版本。 為了進行討論，更新新增了 Visual Studio 的支援，但也可能是較簡單的安全性修補程式或錯誤修正 Service Pack。 Windows Installer 安裝較新元件的規則時，不會重新複製系統上已有的未變更元件。 在此情況下，版本為1.0 的系統會覆寫已更新的元件 Comp_MyVSPackage，並讓使用者選擇使用其元件 Comp_VS2005_Reg 新增功能 Feat_VS2005。

> [!CAUTION]
> 每當 VSPackage 在多個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本之間共用時，VSPackage 的後續版本就必須維持與舊版 Visual Studio 的回溯相容性。 如果您不能維持回溯相容性，就必須使用並存的私用 Vspackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

![VS 共用 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

此案例提供新的 VSPackage 安裝程式，利用 Windows Installer 的次要升級支援。 使用者只要安裝版本1.1，it 就會升級1.0 版。 不過，系統上不需要有1.0 版。 相同的安裝程式將會在沒有1.0 版的系統上安裝1.1 版。 以這種方式提供次要升級的優點是，不需要完成開發升級安裝程式和完整產品安裝程式的工作。 其中一個安裝程式會執行這兩項作業。 安全性修正或 Service Pack 可能會改為利用 Windows Installer 的修補程式。 如需詳細資訊，請參閱[修補和升級](/windows/desktop/Msi/patching-and-upgrades)。

## <a name="scenario-3-side-by-side-vspackage"></a>案例3：並存 VSPackage

此案例提供兩個 VSPackage 安裝程式，每個版本都有一個 Visual Studio .NET 2003 和 Visual Studio。 每個安裝程式都會安裝並存或私用的 VSPackage （特別針對特定版本的 Visual Studio 所建立和安裝的）。 每個 VSPackage 都在自己的元件中。 因此，每個都可以使用修補程式或維護版本來個別提供服務。 由於 VSPackage DLL 現在是特定版本，因此可以安全地將其註冊資訊包含在與 DLL 相同的元件中。

![VS 並存 VS Package 安裝程式](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

每個安裝程式也都包含兩個安裝程式之間共用的程式碼。 如果共用程式碼已安裝到通用位置，則安裝這兩個 .msi 檔案只會安裝共用程式碼一次。 第二個安裝程式只會遞增元件上的參考計數。 參考計數可確保如果卸載其中一個 Vspackage，共用程式碼會保留供其他 VSPackage 之用。 如果也卸載了第二個 VSPackage，共用的程式碼將會被移除。

## <a name="scenario-4-side-by-side-vspackage-update"></a>案例4：並存 VSPackage 更新

在此案例中，您的 VSPackage Visual Studio 會遭受安全性弱點的影響，而且您需要發出更新。 如案例2所示，您可以建立新的 .msi 檔案來更新現有的安裝以包含安全性修正程式，以及部署已備妥安全性修正程式的新安裝。

在此情況下，VSPackage 是安裝在全域組件快取（GAC）中的受控 VSPackage。 當您重建它以包含安全性修正時，您必須變更元件版本號碼的修訂編號部分。 新元件版本號碼的註冊資訊會覆寫先前的版本，導致 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入固定的元件。

![VS 並存 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

如需並存元件部署的詳細資訊，請參閱[使用 .NET Framework 簡化部署和解決 DLL Hell](https://msdn.microsoft.com/library/ms973843.aspx)。

## <a name="see-also"></a>請參閱

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)