---
title: VSPackage 安裝案例 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 819f6b9a1da5979e3e9647d6a0773d741f13e945
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253054"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 安裝案例
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

請務必設計您的 VSPackage 安裝程式的彈性。 例如，您可能需要在未來，發行安全性修補程式，或您可能會變更商務策略，需要完整的並存版本控制支援。  
  
 在 [支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)，您可以閱讀的優點和支援的並排顯示安裝的問題[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]VSPackage 的共用或並排顯示安裝。 簡單地說，並排顯示 Vspackage 提供您最大的彈性來支援新功能[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
 本主題中討論的案例不是您唯一的選擇，但它們會顯示為建議的最佳作法。  
  
## <a name="components-privacy-and-sharing"></a>元件、 隱私權和共用  
  
##### <a name="make-your-components-independent"></a>使您的元件不受影響  
 一旦您找出並填入一個元件，將指派`GUID`，部署元件，您無法變更其組合。 如果您變更元件的組合，產生的元件必須具有新的新元件`GUID`。 根據這些事實，最大的版本控制彈性也同樣適藉由每個元件的獨立、 獨立地單位。 如需規則來控管元件的詳細資訊，請參閱[變更元件的程式碼](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx)並[發生什麼情況元件規則都會中斷，？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>不要混合使用共用和私用元件中的資源  
 參考計數，就會發生在元件層級上。 因此，混合在一個元件中的共用和私用資源無法讓更新私用的資源，例如可執行檔，而不也覆寫共用的資源。 此案例會建立回溯相容性問題，並會限制您建立並排顯示功能。  
  
 登錄值，例如用來註冊使用 VSPackage[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]應該在元件中分開保存用來註冊使用 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 共用的檔案或登錄值會進入另一個元件。  
  
## <a name="scenario-1-shared-vspackage"></a>案例 1： 共用的 VSPackage  
 在此案例中，共用 VSPackage (單一的二進位檔，可支援多個版本的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) 隨附的 Windows Installer 套件。 註冊的每一個版本[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]控制使用者可選取的功能。 這也表示，當指派給不同的功能，每個元件可以選取個別的安裝或解除安裝，讓使用者控制整合的不同版本的 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 (請參閱[Windows Installer 功能](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx)如需有關使用 Windows Installer 封裝中的功能。)  
  
 ![VS 的共用 VSPackage 圖形](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
共用的 VSPackage 安裝程式  
  
 如圖所示，共用的元件都會 Feat_Common 功能，一定會安裝的一部分。 藉由 [Feat_VS2002] 和 [Feat_VS2003] 功能顯示，使用者可以在安裝階段選擇到哪些版本的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]他們想要整合 VSPackage。 使用者也可以使用 Windows 安裝程式的維護模式來新增或移除的功能，在此情況下新增或移除不同版本的 VSPackage 註冊資訊[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
> [!NOTE]
>  將功能顯示資料行設定為 0，會隱藏它。 的低層級的資料行值，例如 1，可確保一律會進行安裝。 如需詳細資訊，請參閱 < [INSTALLLEVEL 屬性](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx)並[特徵資料表](http://msdn.microsoft.com/library/aa368585.aspx)。  
  
## <a name="scenario-2-shared-vspackage-update"></a>案例 2： 共用 VSPackage 更新  
 在此案例中，出貨 VSPackage 安裝案例 1 中的更新的版本。 討論中，更新會新增支援[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，但也可能是較簡單安全性修補程式或 bug 修正 service pack。 安裝較新的元件的 Windows 安裝程式的規則需要變更的元件已經在系統上不會重新複製。 在此情況下，具有已存在的 1.0 版的系統會覆寫更新的元件 Comp_MyVSPackage.dll，並且讓使用者選擇加入新的功能 Feat_VS2005 Comp_VS2005_Reg 其元件。  
  
> [!CAUTION]
>  每當多個版本之間的共用 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，它是基本的 VSPackage 的後續版本維護與舊版的回溯相容性[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 您無法維護回溯相容性，您必須使用並排顯示的私用的 Vspackage。 如需詳細資訊，請參閱 <<c0> [ 支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
 ![VS 共用的 VS 套件更新影像](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
共用 VSPackage 更新安裝程式  
  
 本案例說明新 VSPackage 的安裝程式，善用 Windows 安裝程式支援針對次要升級。 使用者只要安裝 1.1 版，而它將會升級版本 1.0。 不過，不需要有系統上的 1.0 版。 相同的安裝程式會安裝沒有 1.0 版的系統上的 1.1 版。 提供次要升級，以這種方式的優點是不需要經過開發升級的安裝程式和完整產品安裝程式的工作。 一個安裝程式會執行兩項作業。 安全性修正程式或服務套件可能會改為利用 Windows Installer 修補程式。 如需詳細資訊，請參閱 <<c0> [ 修補和升級](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)。  
  
## <a name="scenario-3-side-by-side-vspackage"></a>案例 3： 並排顯示 VSPackage  
 本案例說明兩個 VSPackage 的安裝程式，其中每個版本的 Visual Studio.NET 2003年和[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 每個安裝程式安裝的側邊或私用，VSPackage (特別建置並安裝特定版本的其中一個[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)])。 每個 VSPackage 都處於其本身的元件。 因此，每個可個別服務修補程式或維護版本。 因為 VSPackage DLL 現在是版本專屬，很安全地與 DLL 相同的元件中包含其登錄資訊。  
  
 ![VS 端&#45;的&#45;端的 VS 套件圖形](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
並排顯示 VSPackage 的安裝程式  
  
 每個安裝程式也會包含兩個安裝程式之間共用的程式碼。 如果共用的程式碼安裝到通用位置後，安裝這兩個.msi 檔案會安裝共用的程式碼一次。 第二個安裝程式只會遞增參考計數，在元件上。 參考計數可確保，如果解除安裝 Vspackage 的其中一個時，共用程式碼將會保持其他 vspackage。 如果第二個的 VSPackage 會以及解除安裝，將會移除共用的程式碼。  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>案例 4： 並排顯示 VSPackage 更新  
 在此案例中，為 VSPackage[!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]發生從安全性弱點，並且您要發行一項更新。 案例 2，您可以建立新的.msi 檔案，以更新現有的安裝，包括安全性問題修正，以及部署新安裝安全性修正程式已經就緒。  
  
 在此情況下，VSPackage 是安裝在全域組件快取 (GAC) 中的 managed 的 VSPackage。 當您重建其包含安全性修正程式時，您必須變更組件版本號碼的修訂編號部分。 註冊資訊的新組件版本號碼會覆寫先前的版本，導致[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入固定的組件。  
  
 ![VS 端&#45;的&#45;端的 VS 套件更新圖形](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
並排顯示 VSPackage 更新安裝程式  
  
 **附註**如需有關部署的並排顯示組件的詳細資訊，請參閱[簡化部署和使用.NET Framework 解決 DLL Hell](http://msdn.microsoft.com/library/ms973843.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 安裝程式](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [支援多個 Visual Studio 版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

