---
title: 共用和版本建立 Vspackage 之間選擇 |Microsoft 文件
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
ms.openlocfilehash: ce7f58d664c6a186146272af16324be2fee90983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104614"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>選擇 共用和版本建立 Vspackage
不同版本的 Visual Studio 可以在相同電腦上並存。 Vspackage 可以支援的任何集合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本。  
  
 您可以啟用 Vspackage 透過兩種策略、 共用的策略或已建立版本的策略來並行安裝。 同時容納多個版本的目前狀態[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和相關聯的版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
 在多個版本中使用共用的策略，在註冊一個 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 已建立版本的策略，在安裝多個 VSPackage Dll，其中每個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支援。  
  
## <a name="shared-vspackages"></a>共用的 Vspackage  
 共用的 VSPackage，則適合使用當您使用相同的 VSPackage 中的多個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 若要實作共用的 VSPackage，您必須採取下列步驟：  
  
-   讓 VSPackage 與多個版本的相容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這麼做的兩種方式是使用：  
  
    -   限制您使用的最早的版本功能的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支援。  
  
    -   程式設計 VSPackage 來適應版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]它正在執行中。 然後，如果較新的服務查詢失敗，VSPackage 可提供較舊的版本所支援的其他服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   適當地登錄 VSPackage。 如需詳細資訊，請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)和[Managed VSPackage 註冊](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。  
  
-   適當地登錄檔案的副檔名。 如需詳細資訊，請參閱[註冊的副檔名來並行部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   建立部署 VSPackage 的適當版本的安裝程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[與 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)和[元件管理](../extensibility/internals/component-management.md)。  
  
-   解決註冊衝突的問題。 如需詳細資訊，請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)。  
  
-   請確定共用和版本化檔案採用參考計數以允許安全的安裝與移除多個版本。 如需詳細資訊，請參閱[元件管理](../extensibility/internals/component-management.md)。  
  
## <a name="versioned-vspackages"></a>已建立版本的 Vspackage  
 已建立版本的 VSPackage 策略，在您建立一個 VSPackage 的每個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支援。 這是適當您預計要充分利用更新的版本所提供的服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，因為每個 VSPackage 可以持續發展，而不會影響其他人。 不過，從單一程式碼基底，或是從多個獨立的程式碼基底，建立多個二進位檔的建立版本的策略將會執行初始共用策略比開發。 此外，其他的安裝程式工作可能需要因為您必須建立個別的安裝，每個版本，或是單一安裝程式偵測到舊版的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]所安裝，以及支援您的 VSPackage。  
  
## <a name="binary-compatibility"></a>二進位碼相容性  
 一般而言，二進位碼相容性可讓使用舊版 Visual Studio 來執行更新版本的 Visual Studio 中開發原生程式碼 Vspackage。 不過，有三個重要的例外狀況：  
  
-   如果您的 VSPackage 依賴特定版本的 common language runtime，則必須判斷在哪些版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]它正在執行。  
  
-   VSPackage 可能會有另一個 VSPackage 或另一個產品的特定功能的相依性。 因此，VSPackage 可以執行只其中相依性符合。  
  
-   VSPackage 可能會受到中的安全性修正[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]service pack 或更新版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 較舊版本，在這些情況下，開發 VSPackage[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]的版本中可能無法執行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已套用安全性問題修正後。 不過，您可以重建您的封裝，以較新版本，讓它也在較早版本中執行。  
  
 Managed 的 Vspackage 必須使用版本建置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]符合的目標版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 除了規劃您的 VSPackage 二進位檔的二進位碼相容性，您也應該考慮解決方案和專案檔案格式。 如果您的 VSPackage 會建立新的專案類型，您必須決定是否可以執行或的多個版本中只有一個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[升級自訂專案](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [元件管理](../extensibility/internals/component-management.md)