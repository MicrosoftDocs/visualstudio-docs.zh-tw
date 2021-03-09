---
title: 遺漏 DA0002-VSPerfCorProf.dll |Microsoft 檔
description: 當使用 profiler 資料集合的命令列工具，而不使用 VSPerfCLREnv 來初始化必要的環境變數，或在分析工具啟動時，如果另一個 profiler 正在執行，就會發生這個警告。
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 763a28dcb2200549b13b3562ffe3ab9fa629cdc5
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466176"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002：遺漏 VSPerfCorProf.dll

|Item|值|
|-|-|
|規則 ID|DA0002|
|類別|分析工具使用方式|
|分析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行分析|
|訊息|在未使用 *VSPerfCLREnv* 適當設定環境變數的情況下，會顯示已收集的檔案。 可能無法解析 Managed 二進位檔的符號。|
|規則型別|資訊|

## <a name="cause"></a>原因
 分析工具在執行程式碼剖析期間找不到 *VSPerfCorProf.dll* 。 當流量分析工具資料集合的命令列工具，而不使用 *VSPerfCLREnv* 來初始化必要的環境變數時，就會發生此警告。 如果在分析工具啟動時正在執行另一個分析工具，也可能會引發警告。

## <a name="rule-description"></a>規則描述
 必須在分析回合之前設定特定環境變數，讓分析工具解決 .NET Framework 二進位檔中的符號。 此警告表示在收集分析資料之前，不會執行 *VSPerfCLREnv .cmd* 工具。 可能無法解析 Managed 二進位檔的符號。 如需從命令列使用程式碼剖析工具的詳細資訊，請參閱 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 當您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中使用命令列工具來分析 Managed 應用程式時，請先執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具，再開始收集資料。
