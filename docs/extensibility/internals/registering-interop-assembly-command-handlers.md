---
title: 註冊 Interop 元件命令處理常式 |Microsoft Docs
description: 深入瞭解使用 Interop 元件的所有 Vspackage 執行命令所使用的基本命令合約。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 641a21658e490f94a27cbd9120d044539a7ec284
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062755"
---
# <a name="registering-interop-assembly-command-handlers"></a>註冊 Interop 組件命令處理常式
VSPackage 必須註冊，才能 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 讓整合式開發環境 (IDE) 適當地路由命令。

 登錄可以透過手動編輯或使用註冊機構 ( .rgs) 檔來更新。 如需詳細資訊，請參閱 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)。

 受控封裝架構 (MPF) 透過類別提供這種功能 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 。

- [命令表格格式參考](/previous-versions/bb164647(v=vs.100)) 資源位於非受控附屬 UI dll 中。

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage 的命令處理常式註冊
 VSPackage 做為使用者介面 (UI) 型命令的處理常式，需要在 VSPackage 後命名的登錄專案 `GUID` 。 此登錄專案會指定 VSPackage 之 UI 資源檔的位置，以及該檔案內的功能表資源。 登錄專案本身位於 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \Menus 下，其中是的 *\<Version>* 版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，例如9.0。

> [!NOTE]
> \\ *\<Version>* 當 shell 初始化時，可使用替代的根目錄覆寫 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio的根路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 如需根路徑的詳細資訊，請參閱 [使用 Windows Installer 安裝 vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 資源登錄專案
 登錄專案的結構如下：

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> 是 VSPackage 的， `GUID` 格式為 {XXXXXX-xxxx-XXXXXXXXX}。

 *\<Resource Information>* 由以逗號分隔的三個元素組成。 這些元素依序為：

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 下表描述的欄位 \<*Resource Information*> 。

| 元素 | 描述 |
|---------------------------| - |
| \<*Path to Resource DLL*> | 這是包含功能表資源之資源 DLL 的完整路徑，也就是空白，表示 VSPackage 的資源 DLL 會在 VSPackage 本身註冊) 的封裝子機碼中指定使用 (。<br /><br /> 建議您將這個欄位保留空白。 |
| \<*Menu Resource ID*> | 這是資源的資源識別碼 `CTMENU` ，其中包含 VSPackage 的所有 UI 元素（從 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) 檔案編譯）。 |
| \<*Menu Version*> | 這是用來作為資源版本的數位 `CTMENU` 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值來判斷它是否需要 remerge 資源的內容 `CTMENU` ，以及其所有資源的快取 `CTMENU` 。 藉由執行 devenv 安裝命令來觸發 remerge。<br /><br /> 此值一開始應該會設定為1，並且在資源的每次變更之後 `CTMENU` 和 remerge 發生之前遞增。 |

### <a name="example"></a>範例
 以下是幾個資源專案的範例：

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>另請參閱
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)