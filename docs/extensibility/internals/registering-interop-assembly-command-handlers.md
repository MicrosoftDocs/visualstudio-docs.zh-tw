---
title: 註冊 Interop 組件命令處理常式 |Microsoft 文件
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
ms.openlocfilehash: a4b2c0d40029cbc84d64a4ffe5ee50c59c893b95
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="registering-interop-assembly-command-handlers"></a>註冊 Interop 組件命令處理常式
VSPackage 必須向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使整合式的開發環境 (IDE) 適當地路由傳送它的命令。  
  
 手動編輯，或使用的註冊機構 (.rgs) 檔案，可以更新登錄。 如需詳細資訊，請參閱[建立登錄器指令碼](/cpp/atl/creating-registrar-scripts)。  
  
 Managed Package Framework (MPF) 提供這項功能透過<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>類別。  
  
 [命令資料表格式參考](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f)資源位於 unmanaged 附屬 UI dll。  
  
## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage 的命令處理常式註冊  
 VSPackage，做為使用者介面 (UI) 的處理常式-根據的命令需要登錄項目命名 VSPackage `GUID`。 此登錄項目指定 VSPackage 的 UI 資源檔和該檔案中的功能表資源的位置。 登錄項目本身位於 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<版本 >*\Menus，其中*\<版本 >*版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，例如 9.0。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路徑\\*\<版本 >*會覆寫以替代根時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層會初始化。 如需根路徑的詳細資訊，請參閱[與 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 的資源登錄項目  
 登錄項目結構是：  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> 是`GUID`{XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX} 形式 VSPackage。  
  
 *\<資源資訊 >*三個以逗號分隔的項目所組成。 這些元素，順序如下：  
  
 \<*資源 DLL 路徑*>， \<*功能表資源識別碼*>， \<*功能表版本*>  
  
 下表描述的欄位\<*資源資訊*>。  
  
|項目|描述|  
|-------------|-----------------|  
|\<*資源 DLL 路徑*>|這是資源包含功能表資源 DLL 的完整路徑，或保留為空白，表示 VSPackage 的資源 DLL 使用 （如同在其中註冊自己的 VSPackage 的封裝子機碼中指定）。<br /><br /> 它是可將此欄位保留空白。|  
|\<*功能表資源識別碼*>|這是資源識別碼`CTMENU`資源，因為從編譯的所有 UI 項目包含 vspackage [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案。|  
|\<*功能表版本*>|這是用做為版本號碼`CTMENU`資源。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值來判斷它是否需要 remerge 內容`CTMENU`快取的所有資源`CTMENU`資源。 Remerge 會觸發執行 devenv 安裝命令。<br /><br /> 這個值應該一開始設定為 1 而且在每次變更後遞增`CTMENU`資源和 remerge 發生之前。|  
  
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