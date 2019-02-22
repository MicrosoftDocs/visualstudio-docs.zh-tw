---
title: 適用於 VSPackage 開發的 Devenv 命令列參數 |Microsoft Docs
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89114689f933f3b09aac1d7ffcec109e81f631ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970548"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>適用於 VSPackage 開發的 Devenv 命令列參數

Visual Studio 可讓開發人員自動化工作，從命令列執行時`devenv.exe`，啟動 Visual Studio IDE 的檔案。  

 工作包括：  

- 在部署應用程式從 IDE 外的預先設計好組態。  

- 自動建置專案使用預設組建設定，或偵錯組態。  

- 在 IDE 外部，全部從載入在特定組態中，IDE。 您也可以自訂啟動 IDE。  

## <a name="guidelines-for-switches"></a>參數的指導方針

Visual Studio 文件說明了使用者層級`devenv`命令列參數。 如需詳細資訊，請參閱 < [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)。 `devenv`工具也支援搭配 VSPackage 開發、 部署和偵錯時非常實用的其他命令列參數。  

| 命令列參數 | 描述 |
|---------------------| - |
| `/ResetSkipPkgs` | 清除所有已加入的使用者想要避免載入有問題的 Vspackage，然後啟動 Visual Studio 的略過載入選項。 SkipLoading 標記的存在會停用 VSPackage 的載入。 清除標記會重新啟用載入 VSPackage。<br /><br /> 此參數不需使用引數。 |
| `/RootSuffix` | 啟動 Visual Studio 中使用替代位置。 Visual Studio SDK 安裝程式所建立的捷徑會執行下列命令：<br /><br /> `devenv /RootSuffix exp`<br /><br /> 在此情況下，`exp`識別與特定的後置字元的位置 (例如`10.0Exp`而不是`10.0`)。 實驗執行個體可讓您偵錯的 VSPackage，分別從您用來撰寫程式碼的 Visual Studio 的執行個體。<br /><br /> 這個參數可能需要識別您已使用 VSRegEx.exe 位置的任何字串。 如需詳細資訊，請參閱 <<c0> [ 實驗的執行個體](../extensibility/the-experimental-instance.md)。 |
| `/SafeMode` | 啟動 Visual Studio 在安全模式中，載入只有預設的 IDE 和服務。 `/SafeMode`參數可防止所有第三方 Vspackage 載入 Visual Studio 啟動時，確保穩定執行。<br /><br /> 此參數不需使用引數。 |
| `/Setup` | 強制 Visual Studio 合併說明功能表、 工具列和所有來自可用 Vspackage 的命令群組的資源中繼資料。 您只能以系統管理員身分執行此命令。 <br /><br /> 此參數不需使用引數。 一般來說，會將 `devenv /Setup` 命令指定為安裝程序的最後一個步驟。 使用`/Setup`參數不會啟動 IDE。|
| `/Splash` | 顯示 Visual Studio 啟動顯示畫面，如往常，然後顯示訊息方塊顯示主要 IDE 之前。 訊息方塊，可讓您研究啟動顯示畫面 （例如，若要檢查的 VSPackage 產品圖示）。<br /><br /> 此參數不需使用引數。 |

## <a name="see-also"></a>另請參閱

- [新增命令列參數](../extensibility/adding-command-line-switches.md)
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)