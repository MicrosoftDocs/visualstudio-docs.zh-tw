---
title: -Log (devenv.exe)
description: 瞭解如何使用記錄 devenv 命令列參數，將所有活動記錄至記錄檔以進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040572"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

將所有活動記錄至記錄檔中，以進行疑難排解。 在您至少呼叫 `devenv /log` 一次之後這個檔案才會出現。 根據預設，記錄檔位於下列位置：

**% APPDATA% \\Microsoft \\ VisualStudio \\** \<Version\> **\\ActivityLog.xml**

其中 \<Version\> 是 Visual Studio 版本。 不過，您可以指定不同的路徑和檔案名稱。

## <a name="syntax"></a>語法

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>引數

- *NameOfLogFile*

  必要。 要儲存到其中的記錄檔完整路徑和名稱。

## <a name="remarks"></a>備註

這個參數必須出現在命令列結尾，位於所有其他參數之後。

系統只會針對您使用 `/Log` 參數開啟的所有 Visual Studio 執行個體寫入記錄。

## <a name="example"></a>範例

此範例指示要記錄至使用者主目錄中的 `MyVSLog.xml` 檔案。

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
