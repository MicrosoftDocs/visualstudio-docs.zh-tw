---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42da279a64f04bca7775440f803e7a26e6bd2dc8
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227300"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

設定用於 IDE 內之文字、貨幣和其他值的預設語言。

## <a name="syntax"></a>語法

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>引數

- *LocaleID*

  必要項。 所指定語言的地區設定識別碼 (LCID)。

## <a name="remarks"></a>備註

載入 IDE，並設定環境的預設自然語言。 此變更保存於工作階段之間，而 IDE 會在 [工具] > [選項] > [環境] > [國際設定] > [語言] 方塊中顯示此變更。

如果您的系統不適用指定的語言，則會忽略 `/LCID` 參數。

下表列出 Visual Studio 所支援語言的 LCID。

|語言|LCID|
|--------------|----------|
|中文 (簡體)|2052|
|和 SharePoint 2010 顯示的|1028|
|英文|1033|
|法文|1036|
|德文|1031|
|義大利文|1040|
|日文|1041|
|韓文|1042|
|西班牙文|3082|

## <a name="example"></a>範例

此範例會載入具有英文資源字串的 IDE。

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [選項對話方塊、環境、國際設定](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)