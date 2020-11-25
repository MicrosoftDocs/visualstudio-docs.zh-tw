---
title: -LCID (devenv.exe)
description: 瞭解如何使用 LCID devenv 命令列參數來設定用於 IDE 內文字、貨幣和其他值的預設語言。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eda3a4d9242655af1b018664273ceb693c7e775c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96043981"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

設定用於 IDE 內之文字、貨幣和其他值的預設語言。

## <a name="syntax"></a>語法

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>引數

- *LocaleID*

  必要。 所指定語言的地區設定識別碼 (LCID)。

## <a name="remarks"></a>備註

載入 IDE，並設定環境的預設自然語言。 這項變更會在會話之間保存，IDE 會在 [**工具**  >  **選項**  >  **環境**  >  **國際設定**  >  **語言**] 方塊中顯示這項變更。

如果您的系統不適用指定的語言，則會忽略 `/LCID` 參數。

下表列出 Visual Studio 所支援語言的 LCID。

|語言|LCID|
|--------------|----------|
|簡體中文|2052|
|繁體中文|1028|
|捷克文|1029|
|英文|1033|
|法文|1036|
|德文|1031|
|義大利文|1040|
|日文|1041|
|韓文|1042|
|波蘭文|1045|
|葡萄牙文 (巴西)|1046|
|俄文|1049|
|西班牙文|3082|
|土耳其文|1055

## <a name="example"></a>範例

此範例會載入具有英文資源字串的 IDE。

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [選項對話方塊、環境、國際設定](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)
