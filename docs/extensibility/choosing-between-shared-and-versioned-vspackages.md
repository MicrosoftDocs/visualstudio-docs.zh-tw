---
title: 在共用和版本化的 VS 包之間進行選擇 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739882"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>在分享與版本化 VS 套件之間進行選擇
不同版本的 Visual Studio 可以共存於同一台電腦上。 VS包可以支援任何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]混合版本。

 您可以通過共用策略或版本化策略這兩種策略之一,支援 VSPackages 的並行安裝。 兩者都適應 .NET Framework[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的多個版本和相關版本的存在。

 在分享策略中,一個 VSPackage 註冊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用於多個版本的 。 在版本化策略中,將安裝多個 VSPackage DLL,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每個版本 都安裝一個。

## <a name="shared-vspackages"></a>分享 VS 套件
 在多個版本中使用相同的 VSPackage 時,使用共用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VS 包是合適的。 要實現共用 VS 套件,必須執行以下步驟:

- 使 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]與 的多個版本相容。 有兩種這樣做的方法可用:

  - 將 VSPackage 限制為僅使用您支援的最早[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本的 功能。

  - 對 VSPackage 進行程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]設計, 以適應其運行的版本。 然後,如果對較新的服務的查詢失敗,您的 VSPackage 可以提供舊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本中 支援的其他服務。

- 正確註冊您的 VS 包。 有關詳細資訊,請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)和[託管 VSPackage 註冊](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。

- 正確註冊檔副檔名。 有關詳細資訊,請參閱註冊並行[部署的檔案名副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。

- 建立一個安裝程式,為[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的相應版本部署 VSPackage。 有關詳細資訊,請參閱使用[Windows 安裝程式](../extensibility/internals/installing-vspackages-with-windows-installer.md)和[元件管理](../extensibility/internals/component-management.md)安裝 VS 包。

- 解決註冊衝突問題。 有關詳細資訊,請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)。

- 確保共用檔和版本檔都尊重引用計數,以便安全安裝和刪除多個版本。 有關詳細資訊,請參閱[元件管理](../extensibility/internals/component-management.md)。

## <a name="versioned-vspackages"></a>版本化 VS 套件
 在版本化的 VSPackage 策略下,您可以為每個支援[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本的 VSPackage 創建一個 VSPackage。 當您希望利用更高版本的 服務時,這樣做是合適的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],因為每個 VSPackage 可以在不影響其他版本的情況下發展。 但是,從單個代碼庫或從多個獨立代碼庫創建多個二進位檔的版本化策略可能需要比共用策略更多的初始開發。 此外,可能還需要其他設置工作,因為您必須為每個版本創建單獨的設置,或者創建單個設置,以檢測已安裝的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以及您的 VSPackage 支援的版本。

## <a name="binary-compatibility"></a>二進位相容性
 通常,二進位相容性使使用早期版本的 Visual Studio 開發的本機代碼 VS 包能夠在 Visual Studio 的更高版本中運行。 但是,有三個重要例外:

- 如果您的 VSPackage 依賴於公共語言運行時的特定版本,則[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必須確定 它在哪個版本中正在運行。

- VSPackage 可能依賴於另一個 VSPackage 或其他產品的特定功能。 因此,VSPackage 只能在滿足依賴項時運行。

- VSPackage 可能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]受 服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包或更高版本的安全修補程序的影響。 在這些情況下,使用早期版本的 VSPackage 在應用安全修[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]補程式 後可能無法在版本中運行。 但是,您可以使用更高版本重新生成包,並且使其在早期版本中也運行。

  託管 VS 套件必須使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]和的版本與 的目標[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本匹配。

  除了規劃 VSPackage 二進位檔案的二進位相容性外,還應考慮解決方案和專案檔格式。 如果 VSPackage 創建新的項目類型,則必須決定它是只能在一個版本中運行,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]還是在多個版本中運行。 有關詳細資訊,請參閱[升級自訂專案](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)。

## <a name="see-also"></a>另請參閱
- [使用 Windows 安裝程式安裝 VS 套件](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [元件管理](../extensibility/internals/component-management.md)
