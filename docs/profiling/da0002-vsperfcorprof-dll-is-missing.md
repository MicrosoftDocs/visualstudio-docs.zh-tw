---
title: DA0002-VSPerfCorProf.dll 遺失 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 73cf890ebbee31e2fa681727b0c72e0ce71d3585
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332098"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002：遺漏 VSPerfCorProf.dll

|||
|-|-|
|規則 ID|DA0002|
|類別|分析工具使用方式|
|分析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行分析|
|訊息|該檔案似乎已收集，但未正確設定*VSPerfCLREnv*的環境變數。 可能無法解析 Managed 二進位檔的符號。|
|規則型別|資訊|

## <a name="cause"></a>原因
 分析工具在程式碼剖析執行期間找不到*VSPerfCorProf.dll* 。 當流量分析工具資料集合的命令列工具，而不使用*VSPerfCLREnv*來初始化必要的環境變數時，就會發生此警告。 如果在分析工具啟動時正在執行另一個分析工具，也可能會引發警告。

## <a name="rule-description"></a>規則描述
 必須在分析回合之前設定特定環境變數，讓分析工具解決 .NET Framework 二進位檔中的符號。 此警告表示在收集分析資料之前，不會執行*VSPerfCLREnv .cmd*工具。 可能無法解析 Managed 二進位檔的符號。 如需從命令列流量分析工具的詳細資訊，請參閱[從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 當您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中使用命令列工具來分析 Managed 應用程式時，請先執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具，再開始收集資料。
