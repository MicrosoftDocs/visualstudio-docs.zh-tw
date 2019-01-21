---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52c3576b10fdc88563b3689e4b37d71b7f4659cd
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227547"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

還原 Visual Studio 預設設定，並會自動啟動 Visual Studio IDE。 此參數會選擇性地將設定重設為指定的設定檔案。

第一次啟動 Visual Studio 時，預設設定會來自所選取的設定檔。

> [!TIP]
> 若要了解如何使用整合式開發環境 (IDE) 重設設定，請參閱[重設設定](../environment-settings.md#reset-settings)。

## <a name="syntax"></a>語法

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>引數

- *SettingsFile*

  選擇性。 要套用至 Visual Studio 之設定檔案的完整路徑和名稱。

- *DefaultCollectionSpecifier*

  選擇性。 表示要還原之預設設定集合的指定名稱。 選擇表格中所列的其中一個預設集合指定名稱。

  | 預設集合名稱 | 集合指定名稱 |
  | --- | --- |
  | **一般** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web 開發** | `Web` |
  | **Web 開發 (僅限程式碼)** | `WebCode` |

## <a name="remarks"></a>備註

如果未指定 *SettingsFile*，IDE 就會使用現有的設定來開啟。

## <a name="example"></a>範例

第一個範例會套用 `MySettings.vssettings` 檔案中所儲存的設定。

第二個範例會還原 Visual C# 預設設定檔。

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>另請參閱

- [環境設定](../environment-settings.md)
- [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)