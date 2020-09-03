---
title: 適用于 VSPackage 開發的 Devenv 命令列參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185284"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>適用於 VSPackage 開發的 Devenv 命令列參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可讓開發人員在執行 devenv.exe 時，從命令列將工作自動化， (IDE) 啟動 Visual Studio 整合式開發環境的檔案。  
  
 工作包括：  
  
- 從 IDE 外部將應用程式部署在預先設計的設定中。  
  
- 使用預設組建設定或 debug 設定，自動建立專案。  
  
- 在特定設定中載入 IDE，全都從 IDE 外部進行。 此外，您可以在啟動時自訂 IDE。  
  
## <a name="guidelines-for-switches"></a>參數的指導方針  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 檔描述使用者層級 devenv 命令列參數。 如需詳細資訊，請參閱 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)。 Devenv 也支援適用于 VSPackage 開發、部署和偵錯工具的其他命令列參數。  
  
|命令列參數|描述|  
|--------------------------|-----------------|  
|/safemode|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]以安全模式啟動，僅載入預設的 IDE 和服務。 /Safemode 參數會在啟動時防止載入所有協力廠商 Vspackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，進而確保穩定執行。<br /><br /> 此參數不需使用引數。|  
|/resetskippkgs|清除所有想要避免載入有問題的 Vspackage，然後啟動的使用者已新增的略過載入選項 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 SkipLoading 標記的存在會停用 VSPackage 的載入。 清除標記會重新啟用 VSPackage 的載入。<br /><br /> 此參數不需使用引數。|  
|/rootsuffix|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]使用替代位置開始。 下列命令是由安裝程式所建立的快捷方式所執行 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ：<br /><br /> devenv/RootSuffix exp<br /><br /> 在此情況下，exp 會識別具有特定尾碼的位置，例如 10.0 Exp，而不是10.0。 實驗實例可讓您將 VSPackage 與 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 用來撰寫程式碼的實例分開地進行偵錯工具。<br /><br /> 此參數可以採用任何可識別您使用 VSRegEx.exe 所建立之位置的字串。 如需詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。|  
|/splash|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]如往常般顯示啟動顯示畫面，然後在顯示主要 IDE 之前顯示訊息方塊。 此訊息方塊可讓您研究啟動顯示畫面，以檢查是否有 VSPackage 的產品圖示。<br /><br /> 此參數不需使用引數。|  
  
## <a name="see-also"></a>另請參閱  
 [新增命令列參數](../extensibility/adding-command-line-switches.md)   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
