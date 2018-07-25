---
title: 共用和建立版本的 Vspackage 之間做選擇 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d81aa731a12dedc1237d8af661c718930318f8cd
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231490"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>共用和建立版本的 Vspackage 之間進行選擇
不同版本的 Visual Studio 可以在相同電腦上並存。 Vspackage 可以支援任何混合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本。  
  
 您可以啟用透過兩種策略、 共用的策略或版本控制策略的並排顯示安裝的 Vspackage。 同時容納多個版本存在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]相關聯的版本和[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
 在共用的策略中，以用於多個版本的註冊一個 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在版本控制策略中，安裝多個 VSPackage Dll，其中每個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]您支援。  
  
## <a name="shared-vspackages"></a>共用的 Vspackage  
 當您使用相同的 VSPackage 中的多個版本時使用的共用的 VSPackage 是適當[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 若要實作共用的 VSPackage，您必須採取下列步驟：  
  
-   讓 VSPackage 與多個版本的相容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這麼做的兩種方式是可用：  
  
    -   限制要使用的最舊版本的功能 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]您支援。  
  
    -   程式設計 VSPackage 來適應的新版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中它正在執行。 然後，如果較新的服務的查詢失敗，VSPackage 可以提供其他服務所支援的舊版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   適當地註冊 VSPackage。 如需詳細資訊，請參閱 < [VSPackage 註冊](../extensibility/internals/vspackage-registration.md)並[Managed VSPackage 註冊](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。  
  
-   適當地註冊副檔名。 如需詳細資訊，請參閱 <<c0> [ 註冊並排顯示部署的檔案名稱副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   建立部署的適當版本的 VSPackage 的安裝程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 <<c0> [ 與 Windows 安裝程式的安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)並[元件管理](../extensibility/internals/component-management.md)。  
  
-   解決註冊衝突的問題。 如需詳細資訊，請參閱 < [VSPackage 註冊](../extensibility/internals/vspackage-registration.md)。  
  
-   請確定共用和建立版本的檔案會採用參考計數來允許安全的安裝和移除多個版本。 如需詳細資訊，請參閱 <<c0> [ 元件管理](../extensibility/internals/component-management.md)。  
  
## <a name="versioned-vspackages"></a>建立版本的 Vspackage  
 建立版本的 VSPackage 策略，在您建立的每個版本的一個 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]您支援。 您預計要充分利用的更新版本所提供的服務執行此動作會適當[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，因為每個 VSPackage 不會影響其他人就能持續改進。 不過，從單一程式碼基底，或是從多個獨立的程式碼基底，建立多個二進位檔的版本控制策略可能需要多個初始開發也比共用的策略。 此外，因為您必須建立個別的安裝程式，每個版本或是單一安裝程式偵測到的版本的其他設定工作可能會需要[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]所安裝，以及支援 VSPackage。  
  
## <a name="binary-compatibility"></a>二進位碼相容性  
 一般而言，二進位碼相容性可讓原生程式碼使用舊版的 Visual Studio 執行更新版本的 Visual Studio 中開發的 Vspackage。 不過，有三個重要的例外狀況：  
  
-   如果 VSPackage 依賴特定版本的 common language runtime，則必須判斷哪一個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]它正在執行。  
  
-   VSPackage 可能會有另一個 VSPackage 或其他產品的特定功能的相依性。 因此，VSPackage 可以僅在滿足相依性，才執行。  
  
-   VSPackage 可能會受到在安全性修正[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]service pack 或更新版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 以較早版本的在這些情況下，開發 VSPackage[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]版本中可能無法執行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]套用的安全性修正方法之後。 不過，您可以重建您的套件與較新版本，並將它也在較早版本中執行。  
  
 Managed 的 Vspackage 必須使用的版本來建置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]而[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]符合的目標版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 除了規劃您的 VSPackage 二進位檔二進位碼相容性，您也應該考慮的方案和專案檔案格式。 如果 VSPackage 建立新的專案類型，您必須決定是否可以執行在只有一個版本，或在多個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 <<c0> [ 升級自訂專案](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [元件管理](../extensibility/internals/component-management.md)