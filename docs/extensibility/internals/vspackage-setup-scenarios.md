---
title: "VSPackage 安裝案例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 452a5cfee55bd314bb062d2d1ddd8496593190fa
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例

請務必設計您的 VSPackage 安裝程式的彈性。 例如，您可能需要在未來，發行安全性修補程式或您可能會變更商務策略，需要完整的並存版本控制支援。

在[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)，您可以閱讀的優點和支援的來並行安裝問題[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 的共用或並存安裝。 簡單地說，來並行 Vspackage 提供您最大的彈性來支援新功能的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

本主題中討論的案例不是唯一的選擇，但它們會顯示為建議的最佳作法。

## <a name="components-privacy-and-sharing"></a>元件、 隱私權和共用

### <a name="make-your-components-independent"></a>讓您的元件的獨立

一旦您找出並填入元件時，指派`GUID`，並將此元件部署，您無法變更其構造。 如果您不要變更元件的組合，將產生的元件必須是新的元件，與新`GUID`。 假設這些事實，就藉由每個元件的獨立、 self-reliant 單元會提供版本設定最大的彈性。 如需元件的規則的詳細資訊，請參閱[變更元件的程式碼](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx)和[發生什麼情況元件規則都會中斷？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>請勿混用共用和私用元件中的資源

參考計數，就會發生在元件層級上。 因此，混合在一個元件中的共用和私用的資源，使得更新私用的資源，例如可執行檔，而不也覆寫共用的資源。 此案例會建立回溯相容性問題，並會限制您建立的並行功能。

登錄值，例如用來註冊 VSPackage 與[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]應該保留在元件中其中一個用來與 Visual Studio 註冊 VSPackage 分開。 共用的檔案或登錄值放在另一個元件。

## <a name="scenario-1-shared-vspackage"></a>案例 1： 共用的 VSPackage

在此案例中，共用 VSPackage （單一的二進位檔，可支援多個版本的 Visual Studio 隨附於 Windows Installer 封裝。 註冊 Visual Studio 的每個版本會控制使用者可選取的功能。 這也表示，當指派給個別的功能，每個元件可以被選取個別的安裝或解除安裝，讓使用者控制整合的不同版本的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 (請參閱[Windows Installer 功能](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx)如需有關使用 Windows Installer 封裝中的功能。)

![VS 共用 VSPackage installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

如下圖所示，共用的元件都會 Feat_Common 功能，一定會安裝的一部分。 所顯示的 Feat_VS2002 和 Feat_VS2003 功能，使用者可以選擇在安裝期間到哪些版本的 Visual Studio，他們想要整合 VSPackage。 使用者也可以新增或移除的功能，在此情況下加入或移除 VSPackage 註冊資訊從不同版本的 Visual Studio 中使用 Windows Installer 維護模式。

> [!NOTE]
> 將功能的顯示資料行設定為 0，會隱藏它。 低層級的資料行值，例如 1，可確保永遠都會安裝。 如需詳細資訊，請參閱[INSTALLLEVEL 屬性](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx)和[功能資料表](http://msdn.microsoft.com/library/aa368585.aspx)。

## <a name="scenario-2-shared-vspackage-update"></a>案例 2： 共用的 VSPackage 更新

在此案例中，隨附在案例 1 VSPackage 安裝程式的更新的版本。 討論中，更新會加入支援 Visual Studio 中，但它可能也比較簡單的安全性修補程式或修正 bug 的 service pack。 較新的元件安裝的 Windows Installer 規則需要變更的元件已經在系統上不會重新複製。 在此情況下，已經存在的 1.0 版的系統將會覆寫更新的元件 Comp_MyVSPackage.dll，並且讓使用者選擇加入新的功能 Feat_VS2005 Comp_VS2005_Reg 其元件。

> [!CAUTION]
> 每當多個版本之間的共用 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，很重要的 VSPackage 的後續版本維持回溯相容性的先前版本的 Visual Studio。 在您不能維持回溯相容性，您必須使用-並存的、 私用的 Vspackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

![VS 共用的 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

此案例中呈現新 VSPackage 的安裝程式，利用 Windows 安裝程式支援的次要升級。 使用者只要安裝 1.1 版與升級版本 1.0。 不過，不需要有系統上的 1.0 版。 相同的安裝程式將 1.0 版的系統上安裝 1.1 版。 提供以這種方式的次要升級的優點是不需要經過開發升級的安裝程式和完整產品安裝程式的工作。 一個安裝程式會執行這兩個作業。 安全性修正程式或服務組件可能會改為利用 Windows Installer 修補程式。 如需詳細資訊，請參閱[修補和升級](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)。

## <a name="scenario-3-side-by-side-vspackage"></a>案例 3:-並存 VSPackage

此案例中會呈現兩個 VSPackage 安裝程式，其中每個版本的 Visual Studio.NET 2003年和 Visual Studio。 每個安裝程式會安裝由並存或私用，VSPackage （，特別是建立與特定版本的 Visual Studio 安裝一個）。 每個 VSPackage 為自己元件中。 因此，每個可個別服務修補程式或維護釋放。 VSPackage DLL 現在是特定版本，因為它是安全地與 DLL 相同元件中包含其登錄資訊。

![VS 並存的 VS 套件安裝程式](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

每個安裝程式也包含兩個安裝程式之間共用的程式碼。 如果一般位置安裝共用的程式碼，安裝這兩個.msi 檔案將會安裝共用的程式碼一次。 第二個安裝程式只會遞增參考計數在元件上。 參考計數可確保如果 Vspackage 的其中一個解除安裝，共用的程式碼會保留其他 vspackage。 如果第二個 VSPackage 以及解除安裝，將會移除共用的程式碼。

## <a name="scenario-4-side-by-side-vspackage-update"></a>案例 4:-並存 VSPackage 更新

在此案例中，VSPackage for Visual Studio 仍有安全性弱點，您要發行的更新。 如同案例 2 中，您可以建立新的.msi 檔案，以更新包括安全性問題修正，以及部署新安裝的安全性問題修正已備妥的現有安裝。

在此情況下，VSPackage 是安裝在全域組件快取 (GAC) 中的 managed 的 VSPackage。 當您重建它包含安全性修正程式時，您必須變更組件版本號碼的修訂編號部分。 註冊資訊的新組件版本號碼會覆寫先前的版本，導致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入固定的組件。

![VS 並存的 VS 套件更新安裝程式](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

並存組件的部署的詳細資訊，請參閱[簡化部署和以.NET Framework 解決 DLL Hell](http://msdn.microsoft.com/library/ms973843.aspx)。

## <a name="see-also"></a>請參閱

[Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)  
[支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)