---
title: 以 VSPackage 開發的 Devenv 命令線交換機 |微軟文件
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712198"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>以 VSPackage 開發的 Devenv 指令列交換器

可視化工作室允許開發人員在執行啟動`devenv.exe`Visual Studio IDE 的檔時自動執行命令列的任務。

 工作包括:

- 從IDE外部部署預設計配置中的應用程式。

- 使用預設生成設置或調試配置自動生成專案。

- 在特定配置中載入 IDE,全部來自 IDE 外部。 您還可以在啟動時自定義 IDE。

## <a name="guidelines-for-switches"></a>開關指南

Visual Studio 文件描述了`devenv`使用者級 命令列交換機。 有關詳細資訊,請參閱[Devenv 命令列開關](../ide/reference/devenv-command-line-switches.md)。 該工具`devenv`還支援其他命令行交換機,這些開關對 VSPackage 開發、部署和調試非常有用。

| 命令列開關 | 描述 |
|---------------------| - |
| `/ResetSkipPkgs` | 清除希望避免載入有問題的 VS 包的使用者添加的所有跳過載入選項,然後啟動 Visual Studio。 跳過載入標記的存在會禁用 VSPackage 的載入。 清除標記可重新啟用 VSPackage 的載入。<br /><br /> 此參數不需使用引數。 |
| `/RootSuffix` | 使用備用位置啟動可視化工作室。 以下指令由 Visual Studio SDK 安裝程式建立的快捷方式執行:<br /><br /> `devenv /RootSuffix exp`<br /><br /> 在這種情況下,`exp`識別具有特定後置尾的位置(`10.0Exp`例如`10.0`, 而不是 。 實驗實例允許您將 VSPackage 與用於編寫代碼的 Visual Studio 實例分開調試。<br /><br /> 此開關可以採用任何使用 VSRegEx.exe 識別已建立位置的字串。 有關詳細資訊,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。 |
| `/SafeMode` | 在安全模式下啟動 Visual Studio,僅載入預設 IDE 和服務。 該`/SafeMode`交換機可防止所有第三方 VSPackages 在 Visual Studio 啟動時載入,從而確保穩定執行。<br /><br /> 此參數不需使用引數。 |
| `/Setup` | 強制 Visual Studio 合併資源中繼資料,這些中繼資料描述所有可用 VSPackages 中的選單、工具列和命令組。 您只能以管理員身份執行此命令。 <br /><br /> 此參數不需使用引數。 一般來說，會將 `devenv /Setup` 命令指定為安裝程序的最後一個步驟。 使用`/Setup`交換機不會啟動IDE。|
| `/Splash` | 像往常一樣顯示可視化工作室初始螢幕,然後在顯示主 IDE 之前顯示一個消息框。 消息框允許您研究初始螢幕(例如,檢查 VSPackage 產品圖示)。<br /><br /> 此參數不需使用引數。 |

## <a name="see-also"></a>另請參閱

- [新增命令列交換器](../extensibility/adding-command-line-switches.md)
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
