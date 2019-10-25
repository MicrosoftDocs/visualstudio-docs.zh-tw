---
title: 註冊 Interop 元件命令處理常式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724695"
---
# <a name="registering-interop-assembly-command-handlers"></a>註冊 Interop 組件命令處理常式
VSPackage 必須向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 註冊，以便整合式開發環境（IDE）適當地路由其命令。

 您可以手動編輯或使用註冊機構（.rgs）檔案來更新登錄。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

 Managed Package Framework （MPF）透過 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 類別提供這種功能。

- [命令資料表格式參考](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f)資源位於非受控附屬 UI dll 中。

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage 的命令處理常式註冊
 作為以使用者介面（UI）為基礎之命令處理常式的 VSPackage，需要在 VSPackage `GUID` 之後命名的登錄專案。 此登錄專案會指定 VSPackage 之 UI 資源檔的位置，以及該檔案內的功能表資源。 登錄專案本身位於 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \Menus，其中 *\<Version >* 是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的版本，例如9.0。

> [!NOTE]
> 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell 初始化時，可以使用替代根目錄覆寫 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* 的根路徑。 如需根路徑的詳細資訊，請參閱[使用 Windows Installer 安裝 vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 資源登錄專案
 登錄專案的結構如下：

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> 是以 {XXXXXX-XXXX-XXXXXXXXX} 形式 VSPackage 的 `GUID`。

 *\<Resource 資訊 >* 由三個以逗號分隔的元素所組成。 這些元素的順序如下：

 \< 的*資源 DLL 路徑*>，\<*功能表資源識別碼*>，\<*功能表版本*>

 下表描述 > \<*資源資訊*的欄位。

| 項目 | 描述 |
|---------------------------| - |
| \<*資源 DLL 的路徑*> | 這是包含功能表資源之資源 DLL 的完整路徑，或保留空白，表示將使用 VSPackage 的資源 DLL （如 VSPackage 本身註冊所在的封裝子機碼中所指定）。<br /><br /> 將此欄位保留空白是慣用的。 |
| \<*功能表資源識別碼*> | 這是 `CTMENU` 資源的資源識別碼，其中包含從[.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案編譯之 VSPackage 的所有 UI 元素。 |
| \<*功能表版本*> | 這是用來做為 `CTMENU` 資源版本的數位。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值來判斷它是否需要 remerge `CTMENU` 資源的內容及其所有 `CTMENU` 資源的快取。 藉由執行 devenv 安裝命令來觸發 remerge。<br /><br /> 此值一開始應設定為1，並在 `CTMENU` 資源的每次變更之後和 remerge 發生之前遞增。 |

### <a name="example"></a>範例
 以下是幾個資源專案的範例：

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>請參閱
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)