---
title: VSPackage 開發的 Devenv Command-Line 參數 |Microsoft Docs
description: 瞭解在執行 devenv.exe （啟動 Visual Studio IDE 的檔案）時，開發人員如何從命令列自動執行工作。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904239"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>適用于 VSPackage 開發的 Devenv 命令列參數

Visual Studio 可讓開發人員在執行時，從命令列自動執行工作 `devenv.exe` ，此檔案會啟動 VISUAL STUDIO IDE。

 工作包括：

- 從 IDE 外部將應用程式部署在預先設計的設定中。

- 使用預設組建設定或 debug 設定，自動建立專案。

- 在特定設定中載入 IDE，全都從 IDE 外部進行。 您也可以在啟動時自訂 IDE。

## <a name="guidelines-for-switches"></a>參數的指導方針

Visual Studio 檔會說明使用者層級的 `devenv` 命令列參數。 如需詳細資訊，請參閱 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)。 此 `devenv` 工具也支援適用于 VSPackage 開發、部署和偵錯工具的其他命令列參數。

| 命令列參數 | 描述 |
|---------------------| - |
| `/ResetSkipPkgs` | 清除所有使用者想要避免載入有問題的 Vspackage，然後開始 Visual Studio 時，所新增的所有略過載入選項。 SkipLoading 標記的存在會停用 VSPackage 的載入。 清除標記會重新啟用 VSPackage 的載入。<br /><br /> 此參數不需使用引數。 |
| `/RootSuffix` | 使用替代位置開始 Visual Studio。 下列命令是由 Visual Studio SDK 安裝程式所建立的快捷方式所執行：<br /><br /> `devenv /RootSuffix exp`<br /><br /> 在此情況下，會 `exp` 識別具有特定尾碼 (的位置，例如， `10.0Exp` 而不是 `10.0`) 。 實驗實例可讓您將 VSPackage 與您用來撰寫程式碼的 Visual Studio 實例分開進行偵錯工具。<br /><br /> 此參數可以採用任何可識別您使用 VSRegEx.exe 所建立之位置的字串。 如需詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。 |
| `/SafeMode` | 以安全模式啟動 Visual Studio，僅載入預設的 IDE 和服務。 `/SafeMode`當 Visual Studio 啟動時，此參數會防止載入所有協力廠商 vspackage，以確保穩定執行。<br /><br /> 此參數不需使用引數。 |
| `/Setup` | 強制 Visual Studio 從所有可用的 Vspackage 合併描述功能表、工具列和命令群組的資源中繼資料。 您只能以系統管理員身分執行此命令。 <br /><br /> 此參數不需使用引數。 一般來說，會將 `devenv /Setup` 命令指定為安裝程序的最後一個步驟。 使用 `/Setup` 參數並不會啟動 IDE。|
| `/Splash` | 如往常般顯示 Visual Studio 啟動顯示畫面，然後在顯示主要 IDE 之前顯示訊息方塊。 訊息方塊可讓您研究啟動顯示畫面 (例如，檢查 VSPackage 產品圖示) 。<br /><br /> 此參數不需使用引數。 |

## <a name="see-also"></a>另請參閱

- [新增命令列參數](../extensibility/adding-command-line-switches.md)
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
