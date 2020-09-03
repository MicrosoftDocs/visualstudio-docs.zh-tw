---
title: -LCID (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672706"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

設定用於整合式開發環境 (IDE) 內文字、貨幣和其他值的預設語言。

## <a name="syntax"></a>語法

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>引數
 需要 `LocaleID`。 所指定語言的 LCID (地區設定識別碼)。

## <a name="remarks"></a>備註
 載入 IDE，並設定環境的預設自然語言。 在工作階段之間會持續保存這項變更，並在 IDE 中，將其反映在 [選項]**** 對話方塊中 [環境]**** 選項的 [國際設定]**** 窗格中。

 如果使用者系統未提供指定的語言，則會忽略 /LCID 參數。

 下表列出 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 所支援語言的 LCID。

|語言|LCID|
|--------------|----------|
|簡體中文|2052|
|繁體中文|1028|
|英文|1033|
|法文|1036|
|德文|1031|
|義大利文|1040|
|日文|1041|
|韓文|1042|
|西班牙文|3082|

## <a name="example"></a>範例
 此範例會載入具有英文資源字串的 IDE。

```
devenv /LCID 1033
```

## <a name="see-also"></a>另請參閱
 [Devenv 命令列切換](../../ide/reference/devenv-command-line-switches.md)[國際設定、環境、選項對話方塊](../../ide/reference/international-settings-environment-options-dialog-box.md)[自訂視窗版面](../../ide/customizing-window-layouts-in-visual-studio.md)配置
