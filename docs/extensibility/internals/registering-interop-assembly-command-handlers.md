---
title: 註冊 Interop 組件命令處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a9bd306f6c43b5facef5c114a99f2ae05e41cce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893776"
---
# <a name="registering-interop-assembly-command-handlers"></a>註冊 Interop 組件命令處理常式
VSPackage 必須向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以便整合式的開發環境 (IDE) 正確地路由傳送它的命令。  

 您可以更新登錄，手動編輯，或使用登錄器 (.rgs) 檔案。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。  

 Managed Package Framework (MPF) 提供這項功能透過<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>類別。  

 [命令資料表格式參考](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f)資源位於未受管理的附屬 UI 的 dll。  

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage 的命令處理常式註冊  
 VSPackage，做為使用者介面 (UI) 的處理常式為基礎的命令需要命名 VSPackage 的登錄項目`GUID`。 此登錄項目指定 VSPackage 的 UI 資源檔和該檔案中的功能表資源的位置。 登錄項目本身位於 hkey_local_machine\software\microsoft\visualstudio \\\*\<版本 >* \Menus，其中*\<版本 >* 是的新版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 9.0。  

> [!NOTE]
>  Hkey_local_machine\software\microsoft\visualstudio \ 的根路徑\\*\<版本 >* 可以覆寫以替代 root 時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell 初始化。 如需詳細的根路徑的詳細資訊，請參閱[使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 的資源登錄項目  
 結構的登錄項目是：  

```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  

 \<*GUID*> 是`GUID`的 VSPackage 中的表單 {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}。  

 *\<資源資訊 >* 三個以逗號分隔的項目所組成。 這些元素，順序如下：  

 \<*資源 DLL 路徑*>， \<*功能表資源識別碼*>， \<*功能表版本*>  

 下表描述的欄位\<*資源資訊*>。  


| 元素 | 描述 |
|---------------------------| - |
| \<*資源 DLL 路徑*> | 這是資源包含的功能表資源 DLL 的完整路徑，或保留為空白，表示 VSPackage 的資源 DLL 使用 （如同在其中自行註冊 VSPackage 的封裝子機碼中指定）。<br /><br /> 它是自訂此欄位空白。 |
| \<*功能表資源識別碼*> | 這是資源識別碼`CTMENU`資源，其中包含所有 UI 項目的 VSPackage 從編譯[.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案。 |
| \<*功能表版本*> | 這是用作為版本編號`CTMENU`資源。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值來判斷它是否需要 remerge 的內容`CTMENU`快取的所有資源`CTMENU`資源。 Remerge 就會觸發執行 devenv 安裝程式命令。<br /><br /> 這個值應該一開始設定為 1 而且在每次變更之後遞增`CTMENU`資源和 remerge 發生之前。 |

### <a name="example"></a>範例  
 以下是幾個資源項目範例：  

```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  

## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)