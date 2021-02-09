---
title: DA0030-收集資料庫專案的階層互動度量 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bfce545cd3e7eb5e13e28ec7d22aaba4f7cbecfd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908742"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030：收集資料庫專案的階層互動度量

|Item|值|
|-|-|
|規則 ID|DA0030|
|類別|分析工具使用方式|
|程式碼剖析方法|取樣|
|訊息|收集多層應用程式的互動度量可協助您了解資料庫使用模式和關鍵資料存取延遲。 請嘗試在啟用 [階層互動分析] 選項的情況下再次分析應用程式。|
|規則型別|資訊|

## <a name="cause"></a>原因
 <xref:System.Data> 方法呼叫大部分是分析資料，您還不會在執行分析中收集階層互動資料。 請考慮再次進行分析，並加入階層互動資料。

## <a name="rule-description"></a>規則描述
 只要位於 System.Data 命名空間 (包括 <xref:System.Data.Linq><xref:System.Data.Linq>) 的函式中有大量活動時，就會引發此規則。

 多層應用程式針對其展示層及資料層使用多層式服務。 資料層通常是一個執行資料庫管理系統 (例如 Microsoft SQL Server) 的個別處理序。 資料層可能甚至與應用程式其餘部分，在不同的電腦上執行。 取樣分析深入探究函式和執行跨處理序或遠端執行的服務。

 分析工具可以收集使用 ADO.NET 服務的非同步呼叫與 Microsoft SQL Server 資料層互動之多層應用程式的計時資訊。 您必須明確啟用「階層互動分析」。 此功能不是預設開啟。

## <a name="how-to-fix-violations"></a>如何修正違規
 此規則僅供參考，可能不需要更正措施。

 如需如何從 Visual Studio IDE 將階層互動資料新增至分析資料的資訊，請參閱[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)。 如需如何從命令列新增至階層互動資料的資訊，請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。
