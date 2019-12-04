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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777747"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002：遺漏 VSPerfCorProf.dll

|||
|-|-|
|規則識別碼|DA0002|
|Category|分析工具使用方式|
|分析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行分析|
|訊息|可能未正確設定 *VSPerfCLREnv.cmd* 的環境變數就收集檔案。 可能無法解析 Managed 二進位檔的符號。|
|規則類型|資訊|

## <a name="cause"></a>原因
 分析工具在分析回合期間找不到 *VSPerfCorProf.dll*。 如果使用收集分析工具資料的命令列工具，而未使用 *VSPerfCLREnv.cmd* 工具來初始化所需的環境變數，則會發生此警告。 如果在分析工具啟動時正在執行另一個分析工具，也可能會引發警告。

## <a name="rule-description"></a>規則描述
 必須在分析回合之前設定特定環境變數，讓分析工具解決 .NET Framework 二進位檔中的符號。 此警告指出在收集分析資料之前未執行 *VSPerfCLREnv.cmd* 工具。 可能無法解析 Managed 二進位檔的符號。 如需從命令列使用分析工具的詳細資訊，請參閱[從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 當您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中使用命令列工具來分析 Managed 應用程式時，請先執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具，再開始收集資料。
