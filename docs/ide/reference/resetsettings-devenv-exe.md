---
title: -ResetSettings (devenv.exe)
description: 瞭解如何使用 ResetSettings devenv 命令列參數來還原 Visual Studio 預設設定，並自動啟動 Visual Studio IDE。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e523738ff23b40c80b5df21d90b582d94c59087f
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724534"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

還原 Visual Studio 預設設定，並會自動啟動 Visual Studio IDE。 此參數可選擇性地將設定重設為指定的設定檔 (`*.vssettings`) 。

第一次啟動 Visual Studio 時，預設設定會來自所選取的設定檔。

> [!TIP]
> 若要了解如何使用整合式開發環境 (IDE) 重設設定，請參閱[重設設定](../environment-settings.md#reset-settings)。

## <a name="syntax"></a>語法

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>引數

- *SettingsFile*

  選擇性。 要套用至 Visual Studio 之檔案的完整路徑和名稱 `.vssettings` 。

- *DefaultCollectionSpecifier*

  選擇性。 表示要還原之預設設定集合的指定名稱。 選擇表格中所列的其中一個預設集合指定名稱。

  | 預設集合名稱 | 集合指定名稱 |
  | --- | --- |
  | **一般** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web 程式開發** | `Web` |
  | **網頁程式開發 (僅限程式碼)** | `WebCode` |

## <a name="remarks"></a>備註

如果未指定 *SettingsFile*，IDE 就會使用現有的設定來開啟。 


## <a name="example"></a>範例

第一個範例會套用 `MySettings.vssettings` 檔案中所儲存的設定。

第二個範例會還原 Visual C# 預設設定檔。

第三個範例也會在套用設定之後關閉 Visual Studio。 您可以附加 `/Command "File.Exit"` 。

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>另請參閱

- [環境設定](../environment-settings.md)
- [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
