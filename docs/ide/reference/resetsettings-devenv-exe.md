---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8f826db0c619e1dfb5811aaf9d0c5ef40093c97
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388659"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

還原 Visual Studio 預設設定，並會自動啟動 Visual Studio IDE。 選擇性地將設定重設為指定的 *vssettings* 檔案。

第一次啟動 Visual Studio 時，選取的設定檔即會決定預設值。

> [!TIP]
> 若要了解如何使用整合式開發環境 (IDE) 重設設定，請參閱[重設設定](../environment-settings.md#reset-settings)。

## <a name="syntax"></a>語法

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>引數

`SettingsFile`

要套用至 Visual Studio 的 *vssettings* 檔案的完整路徑和名稱。

若要還原為一般開發設定的設定檔，請使用 `General`。

## <a name="remarks"></a>備註

如果未指定任何 `SettingsFile`，下一次您啟動 Visual Studio 時，系統將提示您選取預設的設定集合。

## <a name="example"></a>範例

下列命令列會套用儲存在 `MySettings.vssettings` 檔案中的設定。

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>另請參閱

- [環境設定](../environment-settings.md)
- [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)