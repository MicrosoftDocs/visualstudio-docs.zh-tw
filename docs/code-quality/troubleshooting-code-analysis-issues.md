---
title: "程式碼分析問題疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>程式碼分析問題疑難排解
本主題包含下列的 Visual Studio 程式碼分析問題的疑難排解資訊。  
  
-   [Visual Studio 2010 規則集都不會反映在舊版 Visual Studio 中的變更](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 規則集都不會反映在舊版 Visual Studio 中的變更  
 當您建立規則集[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]包含子規則集，則使用較早版本的 Visual Studio 的電腦上的程式碼分析回合中可能無法套用子規則集的變更。 若要解決此問題，您必須強制重寫的父規則集時，所包含的子規則集的規則集。  
  
1.  開啟父系規則設定[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]。  
  
2.  進行變更，例如加入或移除規則，並儲存規則集。  
  
3.  重新開啟規則集，復原變更，並儲存規則集一次。  
  
## <a name="see-also"></a>另請參閱  
 [分析應用程式品質分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)