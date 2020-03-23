---
title: DA0002：遺漏 VSPerfCorProf.dll | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777747"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002：遺漏 VSPerfCorProf.dll

|||
|-|-|
|規則 ID|DA0002|
|類別|分析工具使用方式|
|分析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行分析|
|訊息|似乎檔是在未正確設置*使用 VSPerfCLREnv.cmd*進行的環境變數的情況下收集的。 可能無法解析 Managed 二進位檔的符號。|
|規則型別|資訊|

## <a name="cause"></a>原因
 在分析運行期間，探測器找不到*VSPerfCorProf.dll。* 當使用用於收集探測器資料的命令列工具而不使用*VSPerfCLREnv.cmd*工具初始化必要的環境變數時，將發生此警告。 如果在分析工具啟動時正在執行另一個分析工具，也可能會引發警告。

## <a name="rule-description"></a>規則描述
 必須在分析回合之前設定特定環境變數，讓分析工具解決 .NET Framework 二進位檔中的符號。 此警告表示在收集分析資料之前未運行*VSPerfCLREnv.cmd*工具。 可能無法解析 Managed 二進位檔的符號。 有關使用命令列中的分析工具的詳細資訊，請參閱[命令列中的分析](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 當您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中使用命令列工具來分析 Managed 應用程式時，請先執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具，再開始收集資料。
