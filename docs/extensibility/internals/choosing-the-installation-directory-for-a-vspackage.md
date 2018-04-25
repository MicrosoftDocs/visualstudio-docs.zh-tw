---
title: VSPackage 所選擇的安裝目錄 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>VSPackage 所選擇的安裝目錄
VSPackage，以及其支援的檔案必須是使用者的檔案系統上。 位置取決於 VSPackage 是否受管理或不受管理，您的並存版本控制配置和使用者選擇。  
  
## <a name="unmanaged-vspackages"></a>Unmanaged 的 Vspackage  
 Unmanaged 的 VSPackage 是 COM 伺服器，可以安裝在任何位置。 其登錄資訊必須精確地反映其位置。 安裝程式使用者介面 (UI) 應該提供做為子目錄 ProgramFilesFolder Windows Installer 屬性的預設位置。 例如:   
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\  
  
 應該允許使用者變更來滿足使用者保持小型的開機磁碟分割的預設目錄，並想要安裝另一個磁碟區上的應用程式和工具。  
  
 如果您並存的配置會使用已建立版本的 VSPackage，您可以使用子目錄來儲存不同的版本。 例如:   
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Managed VSPackage  
 Managed 的 Vspackage 也可以安裝在任何位置。 不過，您應該考慮永遠將它們安裝至全域組件快取 (GAC)，以減少組件載入的時間。 因為 managed 的 Vspackage 一律是強式名稱組件，在 GAC 中安裝這些表示只在安裝期間發生的其強式名稱簽章驗證。 安裝在檔案系統中其他位置的強式名稱組件必須具有驗證每次載入其簽章。 當您在 GAC 中安裝 managed 的 Vspackage 時，使用 regpkg 工具 **/assembly**參數寫入登錄項目指向組件的強式名稱。  
  
 如果您在 GAC 以外的位置安裝 managed 的 Vspackage，請遵循先前給 unmanaged Vspackage 選擇的目錄階層的建議。 使用 regpkg 工具**assemblyfile**參數寫入登錄項目指向 VSPackage 組件的路徑。  
  
 如需詳細資訊，請參閱[註冊和取消登錄 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="satellite-dlls"></a>附屬 Dll  
 依照慣例，VSPackage 附屬 Dll，其中包含特定地區設定的資源，位於 VSPackage 目錄的子目錄中。 子目錄會對應到地區設定識別碼 (LCID) 值。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)表示登錄項目控制 where[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實際上會搜尋 VSPackage 的附屬 DLL。 不過，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]嘗試載入附屬 DLL 的 LCID 值，依下列順序命名的子目錄中：  
  
1.  預設 LCID (VS LCID 例如 \1033 代表英文)  
  
2.  預設值與預設次語言 LCID。  
  
3.  系統預設 LCID。  
  
4.  預設子語言使用系統預設 LCID。  
  
5.  美國英文 (。 \1033 或。 \0x409)。  
  
 如果您的 VSPackage DLL 包含資源和 SatelliteDll\DllName 登錄進入點，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]嘗試以上述順序載入它們。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 共用和版本建立 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [Managed 的封裝註冊](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)