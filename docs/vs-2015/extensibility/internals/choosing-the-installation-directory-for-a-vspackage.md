---
title: 選擇 VSPackage 的安裝目錄 |Microsoft Docs
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
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697251"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>選擇 VSPackage 的安裝目錄
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 及其支援的檔案必須位於使用者的檔案系統上。 位置取決於 VSPackage 是受控或非受控、並存的版本控制配置，以及使用者選擇。  
  
## <a name="unmanaged-vspackages"></a>非受控 Vspackage  
 非受控 VSPackage 是可安裝在任何位置的 COM 伺服器。 其註冊資訊必須正確地反映其位置。 您的安裝程式使用者介面 (UI) 應該提供預設位置作為 ProgramFilesFolder Windows Installer 屬性的子目錄。 例如：  
  
 ProgramFilesFolderMyCompany\MyVSPackageProduct\V1.0\  
  
 使用者應允許變更預設目錄，以配合保留小型開機分區的使用者，並偏好在另一個磁片區上安裝應用程式和工具。  
  
 如果您的並存配置使用已建立版本的 VSPackage，您可以使用子目錄來儲存不同的版本。 例如：  
  
 ProgramFilesFolderMyCompany\MyVSPackageProduct\V1.0\2002\  
  
 ProgramFilesFolderMyCompany\MyVSPackageProduct\V1.0\2003\  
  
 ProgramFilesFolderMyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Managed VSPackage  
 受控 Vspackage 也可安裝在任何位置。 不過，您應該考慮一律將它們安裝到全域組件快取 (GAC) 以減少元件載入時間。 由於 managed Vspackage 一律是強式名稱的元件，因此在 GAC 中安裝它們表示其強式名稱簽章驗證只會在安裝時進行。 在檔案系統中的其他位置安裝的強式名稱元件必須在每次載入時驗證其簽章。 當您在 GAC 中安裝 managed Vspackage 時，請使用 regpkg 工具的 **/assembly** 參數來寫入指向元件強式名稱的登錄專案。  
  
 如果您將 managed Vspackage 安裝在 GAC 以外的位置，請遵循針對非受控 Vspackage 所提供的先前建議來選擇目錄階層。 使用 regpkg 工具的 **/codebase** 參數，寫入指向 VSPackage 元件路徑的登錄專案。  
  
 如需詳細資訊，請參閱 [註冊和取消註冊 vspackage](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="satellite-dlls"></a>附屬 DLL  
 依照慣例，VSPackage 附屬 Dll （其中包含特定地區設定的資源）位於 VSPackage 目錄的子目錄中。 子目錄會對應至地區設定識別碼 (LCID) 值。  
  
 [管理 vspackage](../../extensibility/managing-vspackages.md) 表示登錄專案會控制 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 實際尋找 VSPackage 附屬 DLL 的位置。 但是，會 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 嘗試以下列順序，在名為的子目錄中載入附屬 DLL （以 LCID 值命名）：  
  
1. 預設 LCID (VS LCID，例如 \ 1033 的英文)   
  
2. 預設語言為預設的 LCID。  
  
3. 系統預設的 LCID。  
  
4. 具有預設語言的系統預設 LCID。  
  
5. 美國英文 (. \ 1033 或 .\0x409) 。  
  
   如果您的 VSPackage DLL 包含資源，而 SatelliteDll\DllName 登錄專案指向它，則 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會嘗試以上述順序載入它們。  
  
## <a name="see-also"></a>另請參閱  
 [在共用和建立版本的 Vspackage 之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [受控套件註冊](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
