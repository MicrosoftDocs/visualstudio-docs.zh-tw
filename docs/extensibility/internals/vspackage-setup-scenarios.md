---
title: VSPackage 安裝案例 |Microsoft Docs
description: 深入瞭解使用 VSPackage 的共用或並存安裝來支援 Visual Studio 並存安裝的最佳作法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97538be6c174f76072a6ca006db6443aa3fcdb57
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487968"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例

請務必為您的 VSPackage 安裝程式設計彈性。 例如，您可能需要在未來發行安全性修補程式，或者您可能變更需要完整並存版本控制支援的商務策略。

在 [支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)中，您可以閱讀 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 VSPackage 的共用或並存安裝來支援並存安裝的優點和問題。 簡而言之，並存 Vspackage 提供您最大的彈性來支援的新功能 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

本主題所討論的案例並不是您唯一的選擇，但會顯示為建議的最佳做法。

## <a name="components-privacy-and-sharing"></a>元件、隱私權和共用

### <a name="make-your-components-independent"></a>使元件獨立

一旦您識別並擴展元件、指派和 `GUID` 部署元件之後，就無法變更其組合。 如果您變更元件的組合，則產生的元件必須是具有新元件的新元件 `GUID` 。 基於這些事實，藉由讓每個元件獨立、自我相依的單位，提供最大的版本控制彈性。 如需有關管理元件之規則的詳細資訊，請參閱 [變更元件程式碼](/windows/desktop/Msi/changing-the-component-code) ，以及 [元件規則中斷時會發生什麼事？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>請勿在元件中混合共用和私用資源

參考計數會在元件層級上進行。 因此，將共用和私人資源混合在一個元件中，就無法更新私用資源（例如可執行檔），也不會覆寫共用資源。 此案例會建立回溯相容性問題，並限制您無法建立並存功能。

例如，用來向註冊您的 VSPackage 的登錄值 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 應該保留在不同的元件中，以用來向 Visual Studio 註冊您的 VSPackage。 共用檔案或登錄值仍會移至另一個元件。

## <a name="scenario-1-shared-vspackage"></a>案例1：共用 VSPackage

在此案例中，共用 VSPackage (單一二進位檔，以支援多個版本的 Visual Studio 會隨附于 Windows Installer 套件中。 註冊每個版本的 Visual Studio 是由使用者可選取的功能所控制。 這也表示當指派給不同的功能時，每個元件都可以個別選取以進行安裝或卸載，讓使用者能夠控制將 VSPackage 整合至不同版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。  (請參閱 [Windows Installer 功能](/windows/desktop/Msi/windows-installer-features) ，以取得在 Windows Installer 套件中使用功能的詳細資訊 ) 

![VS Shared VSPackage 安裝程式](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

如圖所示，共用元件會成為 Feat_Common 功能的一部分，而且一律會進行安裝。 藉由讓 Feat_VS2002 和 Feat_VS2003 功能顯示，使用者可以在安裝期間選擇要 VSPackage 整合的 Visual Studio 版本。 使用者也可以使用 Windows Installer 維護模式來新增或移除功能，在此案例中，會從不同版本的 Visual Studio 新增或移除 VSPackage 註冊資訊。

> [!NOTE]
> 將功能的顯示資料行設定為0會隱藏它。 低層級的資料行值（例如1）可確保一律會安裝它。 如需詳細資訊，請參閱 [INSTALLLEVEL 屬性](/windows/desktop/Msi/installlevel) 和 [功能表](/windows/desktop/Msi/feature-table)。

## <a name="scenario-2-shared-vspackage-update"></a>案例2：共用 VSPackage 更新

在此案例中，會在案例1中推出 VSPackage 安裝程式的更新版本。 為了討論，更新新增了 Visual Studio 的支援，但它也可以是較簡單的安全性修補程式或 bug 修正 service pack。 Windows Installer 安裝較新元件的規則時，不會重新複製系統上已變更的元件。 在此情況下，版本為1.0 的系統將會覆寫更新的元件 Comp_MyVSPackage.dll，並讓使用者選擇使用其元件 Comp_VS2005_Reg 來新增功能 Feat_VS2005。

> [!CAUTION]
> 每次在多個版本之間共用 VSPackage 時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，VSPackage 的後續版本都必須維持與舊版 Visual Studio 的回溯相容性。 您必須使用並存私用 Vspackage，才能維持回溯相容性。 如需詳細資訊，請參閱 [支援 Visual Studio 的多個版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

![VS Shared VS Package 更新安裝程式](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

此案例提供新的 VSPackage 安裝程式，利用 Windows Installer 的次要升級支援。 使用者只需安裝1.1 版並升級版本1.0。 不過，系統上並不需要有1.0 版。 相同的安裝程式將會在不含1.0 版的系統上安裝1.1 版。 以這種方式提供次要升級的優點是，您不需要完成開發升級安裝程式和完整產品安裝程式的工作。 一個安裝程式會執行這兩個作業。 安全性修正或 service pack 可能會改為利用 Windows Installer 修補程式。 如需詳細資訊，請參閱 [修補和升級](/windows/desktop/Msi/patching-and-upgrades)。

## <a name="scenario-3-side-by-side-vspackage"></a>案例3：並存 VSPackage

此案例提供兩個 VSPackage 安裝程式—每個版本的 Visual Studio .NET 2003 和 Visual Studio 一個。 每個安裝程式都會安裝並存或私用 VSPackage， (特別針對特定版本的 Visual Studio) 所建立和安裝的安裝程式。 每個 VSPackage 都在自己的元件中。 因此，每個服務都可以使用修補程式或維護版本個別服務。 因為 VSPackage DLL 現在是版本特定的，所以在與 DLL 相同的元件中包含其註冊資訊是安全的。

![VS 並存與套件安裝程式](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

每個安裝程式也包含兩個安裝程式之間共用的程式碼。 如果共用程式碼安裝至一般位置，則安裝這兩個 .msi 檔案只會安裝一次共用程式碼。 第二個安裝程式只會遞增元件的參考計數。 參考計數可確保卸載其中一個 Vspackage 時，共用程式碼會保留給其他 VSPackage。 如果第二個 VSPackage 也已卸載，則會移除共用程式碼。

## <a name="scenario-4-side-by-side-vspackage-update"></a>案例4：並存 VSPackage 更新

在此案例中，您的 Visual Studio VSPackage 會受到安全性弱點的影響，而您必須發出更新。 如同在案例2中，您可以建立新的 .msi 檔案，以更新現有的安裝以包含安全性修正，以及部署已備妥安全性修正程式的新安裝。

在此情況下，VSPackage 是安裝在全域組件快取 (GAC) 的受控 VSPackage。 當您重建它以包含安全性修正時，您必須變更元件版本號碼的修訂編號部分。 新元件版本號碼的註冊資訊會覆寫先前的版本，而導致 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入固定的元件。

![VS 並存與套件更新安裝程式](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

如需並存元件部署的詳細資訊，請參閱 [使用 .NET Framework 簡化部署和解決 DLL Hell](/previous-versions/dotnet/articles/ms973843(v=msdn.10))。

## <a name="see-also"></a>另請參閱

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)