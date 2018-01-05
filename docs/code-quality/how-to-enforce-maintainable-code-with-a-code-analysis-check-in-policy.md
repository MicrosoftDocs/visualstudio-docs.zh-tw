---
title: "如何： 強制執行維護的程式碼與程式碼分析簽入原則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 19d8761abea6934c59673c332ea09e8a0b4e6997
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：以程式碼分析簽入原則強制程式碼的可維護性
開發人員可以使用程式碼度量資訊工具來測量的複雜度和維護的程式碼，但它們不能做為簽入原則的一部分叫用程式碼度量。 不過，小組可以啟用，並強制執行規則，透過簽入原則以符合他們的程式碼的程式碼度量標準的程式碼分析規則。 如需程式碼度量的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。  
  
 開發人員可以啟用的繼承深度、 類別結合程度、 可維護性指數和複雜性規則來強制執行維護的程式碼，透過程式碼分析簽入原則。 這些規則的所有四個程式碼分析原則編輯器中，找到 [可維護性規則] 類別底下。  
  
 系統管理員的版本控制[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]可以加入程式碼分析可維護性規則的簽入原則需求。 這些簽入原則需要開發人員執行程式碼分析簽入初始化之前，根據這些規則變更。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>若要開啟程式碼分析原則編輯器  
  
1.  在**Team Explorer**、 team 專案上按一下滑鼠右鍵、 按一下**Team 專案設定**，然後按一下 **原始檔控制**。  
  
     **原始檔控制** 對話方塊隨即出現。  
  
2.  在**簽入原則**索引標籤，然後按一下**新增**。  
  
     **新增簽入原則** 對話方塊隨即出現。  
  
3.  在**簽入原則**清單中，選取**程式碼分析**核取方塊，然後**確定**。  
  
     **程式碼分析原則編輯器** 對話方塊隨即出現。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>若要啟用程式碼分析可維護性規則  
  
1.  在**程式碼分析原則編輯器**對話方塊的 **規則設定**，依序展開**可維護性規則**節點。  
  
2.  選取核取方塊，下列規則：  
  
    -   繼承深度： **CA1501 AvoidExcessiveInheritance** -臨界值： 警告位於層級的深度超過 5  
  
    -   複雜度： **CA1502 AvoidExcessiveComplexity** -臨界值： 在多個 25 警告  
  
    -   可維護性指數： **ca1505 應 AvoidUnmaintainableCode** -臨界值： 警告少於 20  
  
    -   結合的類別： **CA1506 AvoidExcessiveClassCoupling** -臨界值： 警告位於多個類別 80 和超過 30 方法  
  
    -   此外，如果您想防止組建的規則違規時，選取**將警告視為錯誤**規則說明旁邊的核取方塊。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。 新的簽入原則現在會套用至未來的簽入。  
  
## <a name="see-also"></a>請參閱  
 [程式碼度量值](../code-quality/code-metrics-values.md)   
 [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)