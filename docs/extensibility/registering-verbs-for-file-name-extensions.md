---
title: 註冊檔名副檔名的謂詞 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701538"
---
# <a name="register-verbs-for-file-name-extensions"></a>註冊檔案名副檔名的謂詞
檔名副檔名與應用程式的關聯通常具有使用者按兩下文件時發生的首選操作。 此首選操作連結到與操作對應的謂詞(例如打開)。

 可以使用位於**\{HKEY_CLASSES_ROOTprogid_shell**的 Shell 鍵註冊與程式設計標識符 (ProgID) 關聯的謂詞。 有關詳細資訊,請參考[檔案類型](/windows/desktop/shell/fa-file-types)。

## <a name="register-standard-verbs"></a>註冊標準動詞
 操作系統識別以下標準動詞:

- 開啟

- 編輯

- 播放

- 列印

- 預覽

  只要有可能,註冊一個標準動詞。 最常見的選擇是"打開"謂詞。 僅當打開檔和編輯檔之間存在明顯區別時,才使用 Edit 謂詞。 例如,打開 *.htm*檔會在瀏覽器中顯示它,而編輯 *.htm*檔將啟動 HTML 編輯器。 標準謂詞隨操作系統區域設置進行當地語系化。

> [!NOTE]
> 註冊標準謂詞時,不要為 Open 鍵設置預設值。 預設值包含選單上的顯示字串。 作業系統為標準動詞提供此字串。

 應註冊項目檔以啟動使用者打開檔[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]時的新實例。 下面的示例說明了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]項目的標準謂詞註冊。

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 要在的現有實例中打開檔[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],請註冊 DDEEXEC 密鑰。 下面的範例演示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]*.cs*文件的標準謂詞註冊。

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>設定預設動詞
 默認謂詞是當使用者按兩下 Windows 資源管理員中的檔時執行的操作。 默認謂詞是指定為**\\HKEY_CLASSES_ROOT*progid*_Shell**鍵的預設值的謂詞。 如果未指定值,則預設謂詞是**\\HKEY_CLASSES_ROOT*progid*_Shell**鍵清單中指定的第一個謂詞。

> [!NOTE]
> 如果計劃更改並行部署中擴展的預設謂詞,請考慮對安裝和刪除的影響。 在安裝過程中,將覆蓋原始預設值。

## <a name="see-also"></a>另請參閱
- [管理並行檔案關聯](../extensibility/managing-side-by-side-file-associations.md)
