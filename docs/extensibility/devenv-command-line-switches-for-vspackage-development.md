---
title: 適用於 VSPackage 開發的 Devenv 命令列參數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4333f7e0c892771ffb9b4643f4814cf3352a8f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820289"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>適用於 VSPackage 開發的 Devenv 命令列參數
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可讓開發人員執行時，從命令列的工作自動化*devenv.exe*，啟動 Visual Studio 整合式的開發環境 (IDE) 的檔案。  

 工作包括：  

-   在部署應用程式從 IDE 外的預先設計好組態。  

-   自動建置專案使用預設組建設定，或偵錯組態。  

-   在 IDE 外部，全部從載入在特定組態中，IDE。 此外，您可以自訂啟動 IDE。  

## <a name="guidelines-for-switches"></a>參數的指導方針  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文件會說明使用者層級 devenv 命令列參數。 如需詳細資訊，請參閱 < [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)。 Devenv 也支援搭配 VSPackage 開發、 部署和偵錯時非常實用的其他命令列參數。  


| 命令列參數 | 描述 |
|---------------------| - |
| /safemode | 啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式中，載入只有預設的 IDE 和服務。 /Safemode 參數可防止所有第三方 Vspackage 載入時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會啟動，因而確保穩定執行。<br /><br /> 此參數不需使用引數。 |
| /resetskippkgs | 清除所有略過載入選項已新增的使用者想要避免載入有問題的 Vspackage，然後啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 SkipLoading 標記的存在會停用 VSPackage 的載入。 清除標記會重新啟用載入 VSPackage。<br /><br /> 此參數不需使用引數。 |
| /rootsuffix | 啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用替代位置。 執行下列命令所建立的快顯[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]安裝程式：<br /><br /> devenv /RootSuffix exp<br /><br /> 在此情況下，exp 識別特定的尾碼，例如 10.0Exp，而不是 10.0 的位置。 實驗執行個體可讓您偵錯與執行個體分開 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]您撰寫程式碼使用。<br /><br /> 這個參數可能需要識別您已使用 VSRegEx.exe 建立位置的任何字串。 如需詳細資訊，請參閱 <<c0> [ 實驗的執行個體](../extensibility/the-experimental-instance.md)。 |
| /splash | 顯示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如往常般啟動顯示畫面，並顯示訊息方塊顯示主要 IDE 之前。 訊息方塊，可讓您研究啟動顯示畫面中，檢查 VSPackage 產品圖示，例如。<br /><br /> 此參數不需使用引數。 |

## <a name="see-also"></a>另請參閱  
 [新增命令列參數](../extensibility/adding-command-line-switches.md)   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)