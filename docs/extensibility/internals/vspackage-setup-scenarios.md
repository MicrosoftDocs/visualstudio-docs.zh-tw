---
title: VSPackage 安裝案例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c194588de8dfa8746bb79a8d86bff005d90e7550
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495930"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例

請務必設計您的 VSPackage 安裝程式的彈性。 例如，您可能需要在未來，發行安全性修補程式，或您可能會變更商務策略，需要完整的並存版本控制支援。

在 [支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)，您可以閱讀的優點和支援的並排顯示安裝的問題[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 的共用或並排顯示安裝。 簡單地說，並排顯示 Vspackage 提供您最大的彈性來支援新功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

本主題中討論的案例不是您唯一的選擇，但它們會顯示為建議的最佳作法。

## <a name="components-privacy-and-sharing"></a>元件、 隱私權和共用

### <a name="make-your-components-independent"></a>使您的元件不受影響

一旦您找出並填入一個元件，將指派`GUID`，部署元件，您無法變更其組合。 如果您變更元件的組合，產生的元件必須具有新的新元件`GUID`。 根據這些事實，最大的版本控制彈性也同樣適藉由每個元件的獨立、 獨立地單位。 如需規則來控管元件的詳細資訊，請參閱[變更元件的程式碼](/windows/desktop/Msi/changing-the-component-code)並[發生什麼情況元件規則都會中斷，？](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>不要混合使用共用和私用元件中的資源

參考計數，就會發生在元件層級上。 因此，混合在一個元件中的共用和私用資源無法讓更新私用的資源，例如可執行檔，而不也覆寫共用的資源。 此案例會建立回溯相容性問題，並會限制您建立並排顯示功能。

登錄值，例如用來註冊使用 VSPackage[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]應該分開的元件中用來向 Visual Studio 註冊 VSPackage。 共用的檔案或登錄值會進入另一個元件。

## <a name="scenario-1-shared-vspackage"></a>案例 1： 共用的 VSPackage

在此案例中，共用 VSPackage （單一的二進位檔所支援的 Visual Studio 的多個版本隨附於 Windows 安裝程式封裝中。 向每個版本的 Visual Studio 會控制使用者可選取的功能。 這也表示，當指派給不同的功能，每個元件可以選取個別的安裝或解除安裝，讓使用者控制整合的不同版本的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 (請參閱[Windows Installer 功能](/windows/desktop/Msi/windows-installer-features)如需有關使用 Windows Installer 封裝中的功能。)

![VS 共用 VSPackage 的安裝程式](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

如圖所示，共用的元件都會 Feat_Common 功能，一定會安裝的一部分。 藉由 Feat_VS2002 和 Feat_VS2003 功能顯示，使用者可以選擇在安裝階段到哪些版本的 Visual Studio 中，他們想將 VSPackage。 使用者也可以使用 Windows 安裝程式的維護模式，來新增或移除的功能，在此情況下加入或移除不同版本的 Visual Studio 中的 VSPackage 註冊資訊。

> [!NOTE]
> 將功能顯示資料行設定為 0，會隱藏它。 的低層級的資料行值，例如 1，可確保一律會進行安裝。 如需詳細資訊，請參閱 < [INSTALLLEVEL 屬性](/windows/desktop/Msi/installlevel)並[特徵資料表](/windows/desktop/Msi/feature-table)。

## <a name="scenario-2-shared-vspackage-update"></a>案例 2： 共用 VSPackage 更新

在此案例中，出貨 VSPackage 安裝案例 1 中的更新的版本。 討論中，更新會新增對 Visual Studio 中，但它可能也是更簡單的安全性修補程式或修正的 service pack。 安裝較新的元件的 Windows 安裝程式的規則需要變更的元件已經在系統上不會重新複製。 在此情況下，具有已存在的 1.0 版的系統會覆寫更新的元件 Comp_MyVSPackage.dll，並且讓使用者選擇加入新的功能 Feat_VS2005 Comp_VS2005_Reg 其元件。

> [!CAUTION]
> 每當多個版本之間的共用 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，很重要的 VSPackage 的後續版本維護與舊版 Visual Studio 的回溯相容性。 您無法維護回溯相容性，您必須使用並排顯示的私用的 Vspackage。 如需詳細資訊，請參閱 <<c0> [ 支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

![VS 共用的 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

本案例說明新 VSPackage 的安裝程式，善用 Windows 安裝程式支援針對次要升級。 使用者只要安裝 1.1 版，而它將會升級版本 1.0。 不過，不需要有系統上的 1.0 版。 相同的安裝程式會安裝沒有 1.0 版的系統上的 1.1 版。 提供次要升級，以這種方式的優點是不需要經過開發升級的安裝程式和完整產品安裝程式的工作。 一個安裝程式會執行兩項作業。 安全性修正程式或服務套件可能會改為利用 Windows Installer 修補程式。 如需詳細資訊，請參閱 <<c0> [ 修補和升級](/windows/desktop/Msi/patching-and-upgrades)。

## <a name="scenario-3-side-by-side-vspackage"></a>案例 3： 並排顯示 VSPackage

本案例說明兩個 VSPackage 的安裝程式，其中每個版本的 Visual Studio.NET 2003年和 Visual Studio。 每個安裝程式會安裝的側邊或私用，VSPackage （一個特別建置和安裝 Visual Studio 特定版本）。 每個 VSPackage 都處於其本身的元件。 因此，每個可個別服務修補程式或維護版本。 因為 VSPackage DLL 現在是版本專屬，很安全地與 DLL 相同的元件中包含其登錄資訊。

![VS 並存的 VS 套件安裝程式](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

每個安裝程式也會包含兩個安裝程式之間共用的程式碼。 如果共用的程式碼安裝到通用位置後，安裝這兩個.msi 檔案會安裝共用的程式碼一次。 第二個安裝程式只會遞增參考計數，在元件上。 參考計數可確保，如果解除安裝 Vspackage 的其中一個時，共用程式碼將會保持其他 vspackage。 如果第二個的 VSPackage 會以及解除安裝，將會移除共用的程式碼。

## <a name="scenario-4-side-by-side-vspackage-update"></a>案例 4： 並排顯示 VSPackage 更新

在此案例中，VSPackage 適用於 Visual Studio 仍有安全性弱點，和您要發行一項更新。 案例 2，您可以建立新的.msi 檔案，以更新現有的安裝，包括安全性問題修正，以及部署新安裝安全性修正程式已經就緒。

在此情況下，VSPackage 是安裝在全域組件快取 (GAC) 中的 managed 的 VSPackage。 當您重建其包含安全性修正程式時，您必須變更組件版本號碼的修訂編號部分。 註冊資訊的新組件版本號碼會覆寫先前的版本，導致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入固定的組件。

![VS 並存的 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

如需有關部署的並排顯示組件的詳細資訊，請參閱[簡化部署和使用.NET Framework 解決 DLL Hell](https://msdn.microsoft.com/library/ms973843.aspx)。

## <a name="see-also"></a>另請參閱

[Windows 安裝程式](/windows/desktop/Msi/windows-installer-portal)  
[支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)