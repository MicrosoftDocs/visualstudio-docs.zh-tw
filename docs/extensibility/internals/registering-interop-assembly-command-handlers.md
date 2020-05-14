---
title: 註冊互操作程式集命令處理程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705867"
---
# <a name="registering-interop-assembly-command-handlers"></a>註冊 Interop 組件命令處理常式
VSPackage 必須註冊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 以便整合式開發環境 (IDE) 正確路由其命令。

 註冊表可以通過手動編輯或使用註冊器 (.rgs) 檔進行更新。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

 託管包框架 (MPF)<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>通過 類提供此功能。

- [命令表格式 參考](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f)資源位於非託管的衛星 UI dlls 中。

## <a name="command-handler-registration-of-a-vspackage"></a>命令處理程式 VS 套件註冊
 VSPackage 充噹基於使用者介面 (UI) 的命令的處理程式需要以`GUID`VSPackage 命名的註冊表項。 此註冊表項指定 VSPackage 的 UI 資源檔案的位置以及該檔中的功能表資源。 註冊表項本身位於HKEY_LOCAL_MACHINE\軟體\微軟_VisualStudio\\*\<版本>* \Menus 下,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*\<其中版本>* 是 ,例如 9.0。

> [!NOTE]
> \\*HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio\<版本>* 的根路徑可以在初始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]化 shell 時用備用根覆蓋。 關於根路徑的詳細資訊,請參考[Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 資源註冊表項
 註冊表項的結構是:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID* `GUID`> 是表格 [XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX]中的 VS 包。

 資源資訊>由三個用逗號分隔的元素組成。 * \< * 這些元素按以下順序排列:

 \<*資源 DLL* \<>、*選單資源 ID* \<>、*選單版本的路徑*>

 下表描述了\<*資源資訊*>字段。

| 元素 | 描述 |
|---------------------------| - |
| \<*資源 DLL 路徑*> | 這是包含菜單資源的資源 DLL 的完整路徑,或者該路徑留空,指示將使用 VSPackage 的資源 DLL(如註冊 VSPackage 本身的包子鍵中指定)。<br /><br /> 通常將此欄位留空。 |
| \<*選單資源識別碼*> | 這是`CTMENU`資源的資源 ID,其中包含從[.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案編譯的 VSPackage 的所有 UI 元素。 |
| \<*選單版本*> | 這是用作`CTMENU`資源版本的數位。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用此值確定是否需要將`CTMENU`資源的內容與其`CTMENU`所有資源的緩存重新合併。 通過執行 devenv 設置命令觸發重新合併。<br /><br /> 此值最初應設置為 1,`CTMENU`並在資源中的每一次更改後和重新合併發生之前遞增。 |

### <a name="example"></a>範例
 下面是幾個資源項目的範例:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>另請參閱
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
