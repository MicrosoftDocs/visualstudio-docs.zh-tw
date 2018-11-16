---
title: DA0030：收集資料庫專案的階層互動度量 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16d6275074b3cae6b186fe9bb113e32c33e284af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796749"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030：蒐集資料庫專案的階層互動度量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0030 |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |取樣 |  
|訊息 |收集多層式應用程式的互動度量將協助您了解資料庫使用模式和關鍵資料存取延遲。 嘗試分析應用程式再次啟用 [階層互動分析] 選項。 |  
|規則類型 |資訊 |  
  
## <a name="cause"></a>原因  
 <xref:System.Data> 方法呼叫大部分是分析資料，您還不會在執行分析中收集階層互動資料。 請考慮再次進行分析，並加入階層互動資料。  
  
## <a name="rule-description"></a>規則描述  
 只要位於 System.Data 命名空間 (包括 <xref:System.Data.Linq><xref:System.Data.Linq>) 的函式中有大量活動時，就會引發此規則。  
  
 多層應用程式針對其展示層及資料層使用多層式服務。 資料層通常是一個執行資料庫管理系統 (例如 Microsoft SQL Server) 的個別處理序。 資料層可能甚至與應用程式其餘部分，在不同的電腦上執行。 取樣分析深入探究函式和執行跨處理序或遠端執行的服務。  
  
 分析工具可以收集使用 ADO.NET 服務的非同步呼叫與 Microsoft SQL Server 資料層互動之多層應用程式的計時資訊。 您必須明確啟用「階層互動分析」。 此功能不是預設開啟。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 此規則僅供參考，可能不需要更正措施。  
  
 如需如何從 Visual Studio IDE 將階層互動資料加入分析資料的詳細資訊，請參閱[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)。 如需如何從命令列加入階層互動資料的詳細資訊，請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。



