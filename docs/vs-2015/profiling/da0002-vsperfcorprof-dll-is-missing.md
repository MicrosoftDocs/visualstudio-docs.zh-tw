---
title: DA0002：遺漏 VSPerfCorProf.dll | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54c43143fae898b5a8177d4710bd335e2b8919f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498212"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002：遺漏 VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[DA0002： 遺漏 VSPerfCorProf.dll](https://docs.microsoft.com/visualstudio/profiling/da0002-vsperfcorprof-dll-is-missing)。  
  
規則 Id |DA0002 |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行分析 |  
|訊息 |它會顯示該檔案已收集未正確設定 VSPerfCLREnv.cmd 的環境變數。 可能無法解析 managed 二進位檔的符號。 |  
|規則類型 |資訊 |  
  
## <a name="cause"></a>原因  
 分析工具在分析回合期間找不到 VSPerfCorProf.dll。 如果使用收集分析工具資料的命令列工具，而未使用 VSPerfCLREnv.cmd 工具來初始化所需的環境變數，則會發生此警告。 如果在分析工具啟動時正在執行另一個分析工具，也可能會引發警告。  
  
## <a name="rule-description"></a>規則描述  
 必須在分析回合之前設定特定環境變數，讓分析工具解決 .NET Framework 二進位檔中的符號。 此警告指出在收集分析資料之前未執行 VSPerfCLREnv.cmd 工具。 可能無法解析 Managed 二進位檔的符號。 如需從命令列使用分析工具的詳細資訊，請參閱[從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 當您要在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具中使用命令列工具來分析 Managed 應用程式時，請先執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具，再開始收集資料。



