---
title: 在共用和建立版本的 Vspackage 之間進行選擇 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821983"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>在共用和建立版本的 VSPackage 之間進行選擇
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

不同版本的 Visual Studio 可以並存于同一部電腦上。 Vspackage 可支援任何版本的混合 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
 您可以透過下列兩種策略的其中一種來啟用 Vspackage 的並存安裝：共用策略或已建立版本的策略。 兩者都能容納多個版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和相關聯的版本 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。  
  
 在共用策略中，有一個 VSPackage 會註冊以用於多個版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 在已建立版本的策略中，會安裝多個 VSPackage Dll，您支援的每個版本各有一個 Dll [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
## <a name="shared-vspackages"></a>共用 Vspackage  
 當您在多個版本的中使用相同的 VSPackage 時，使用共用 VSPackage 是適當的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 若要執行共用的 VSPackage，您必須執行下列步驟：  
  
- 讓您的 VSPackage 與多個版本相容 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 有兩種方式可供使用：  
  
  - 將您的 VSPackage 限制為僅使用您支援之最舊版本的功能 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  

  - 將您的 VSPackage 程式設計為適應其執行所在的版本 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 然後，如果較新服務的查詢失敗，您的 VSPackage 可以提供舊版所支援的其他服務 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
- 適當地註冊您的 VSPackage。 如需詳細資訊，請參閱 [VSPackage 註冊](../extensibility/internals/vspackage-registration.md) 和 [受控 VSPackage 註冊](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。  
  
- 適當地註冊副檔名。 如需詳細資訊，請參閱 [註冊並存部署的](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)副檔名。  
  
- 建立安裝程式，以部署適用于適當版本的 VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱使用 Windows Installer 和[元件管理](../extensibility/internals/component-management.md)[安裝 vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 。  
  
- 解決註冊衝突的問題。 如需詳細資訊，請參閱 [VSPackage 註冊](../extensibility/internals/vspackage-registration.md)。  
  
- 確定共用和已建立版本的檔案都採用參考計數，以允許安全地安裝及移除多個版本。 如需詳細資訊，請參閱 [元件管理](../extensibility/internals/component-management.md)。  
  
## <a name="versioned-vspackages"></a>已建立版本的 Vspackage  
 在已建立版本的 VSPackage 策略下，您可以為每個支援的版本建立一個 VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 當您想要利用較新版本所提供的服務時，請這麼做 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，因為每個 VSPackage 都可以在不影響其他專案的情況下演進。 不過，從單一程式碼基底或從多個獨立的程式碼基底建立多個二進位檔的版本控制策略，可能需要比共用策略更多的初始開發。 此外，也可能需要額外的設定工作，因為您必須為每個版本建立個別的設定，或針對偵測 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 已安裝且 VSPackage 支援之版本的單一安裝程式建立個別的設定。  
  
## <a name="binary-compatibility"></a>二進位相容性  
 一般而言，二進位相容性可讓使用舊版 Visual Studio 開發的機器碼 Vspackage 在較新版本的 Visual Studio 中執行。 不過，有三個重要的例外狀況：  
  
- 如果您的 VSPackage 依賴特定版本的 common language runtime，則必須判斷其執行的版本 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
- VSPackage 可能會相依于另一個 VSPackage 或另一個產品的特定功能。 因此，VSPackage 只能在滿足相依性的位置執行。  
  
- VSPackage 可能會受到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] service pack 或更新版本中的安全性修正所影響 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 在這些情況下，使用舊版所開發的 VSPackage [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 可能無法在套用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 安全性修正之後的版本中執行。 不過，您可以使用較新的版本重建套件，並讓它也在舊版中執行。  
  
  Managed Vspackage 必須使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 符合目標版本的和版本來建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
  除了規劃 VSPackage 二進位檔的二進位相容性之外，您也應該考慮方案和專案檔案格式。 如果您的 VSPackage 會建立新的專案類型，您必須決定它是否可以只在一個版本中執行，或在多個版本中執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [升級自訂專案](../misc/upgrading-custom-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [元件管理](../extensibility/internals/component-management.md)
