---
title: 選擇 vspackage 的安裝目錄 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8812ce6eef882f4f1b4effe97320492a34e0f2d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930693"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>選擇 VSPackage 的安裝目錄
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 和其支援的檔案必須是使用者的檔案系統上。 位置取決於 VSPackage 是否管理或未受管理，您的並排顯示版本設定配置和使用者選擇。  
  
## <a name="unmanaged-vspackages"></a>Unmanaged 的 Vspackage  
 Unmanaged 的 VSPackage 是 COM 伺服器可安裝在任何位置。 其登錄資訊必須精確地反映其位置。 安裝程式使用者介面 (UI) 應該提供做為子目錄 ProgramFilesFolder Windows Installer 屬性的預設位置。 例如:   
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\  
  
 應該允許使用者變更預設目錄來容納保持小型的開機磁碟分割的使用者，且想要安裝另一個磁碟區上的應用程式和工具。  
  
 如果您的並排顯示配置使用已建立版本的 VSPackage，您可以使用子目錄來儲存不同的版本。 例如：  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Managed VSPackage  
 Managed 的 Vspackage 也可以安裝在任何位置。 不過，您應該考慮永遠將它們安裝至全域組件快取 (GAC) 中，以減少組件載入時間。 Managed 的 Vspackage 一律是強式名稱組件，因為它們安裝在 GAC 中表示其強式名稱簽章驗證需要只能在安裝階段。 安裝在檔案系統在其他地方的強式名稱組件必須每次載入時驗證其簽章。 當您安裝在 GAC 中的 managed 的 Vspackage 時，使用 regpkg 工具 **/assembly**參數寫入登錄項目指向組件的強式名稱。  
  
 如果您安裝在 GAC 以外的位置中的 managed 的 Vspackage，請依照先前選擇的目錄階層給 unmanaged Vspackage 的建議。 使用 regpkg 工具 **/ 程式碼基底**參數寫入登錄 VSPackage 組件的路徑所指向的項目。  
  
 如需詳細資訊，請參閱 <<c0> [ 註冊和取消註冊 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="satellite-dlls"></a>附屬 Dll  
 依照慣例，VSPackage 附屬 Dll，其中包含為特定地區設定的資源 — 位於 VSPackage 目錄之子目錄中。 子目錄會對應到地區設定識別碼 (LCID) 值。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)指出登錄項目控制 where[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]實際上會尋找 VSPackage 的附屬 DLL。 不過，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]嘗試載入附屬 DLL 中命名的 LCID 值，以下列順序：  
  
1. 預設 LCID (VS LCID，例如適用於英文的 \1033)  
  
2. 使用預設的子語言的預設 LCID。  
  
3. 系統預設 LCID。  
  
4. 預設子語言使用系統預設 LCID。  
  
5. 美國英文 (。 \1033 或。 \0x409)。  
  
   如果您的 VSPackage DLL 包含資源，而 SatelliteDll\DllName 登錄項目指向它，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]嘗試載入它們依上述順序。  
  
## <a name="see-also"></a>另請參閱  
 [共用和建立版本的 Vspackage 之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [受管理的套件註冊](http://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
