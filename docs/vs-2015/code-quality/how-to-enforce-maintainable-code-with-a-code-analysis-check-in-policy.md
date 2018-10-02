---
title: 如何： 強制可維護的程式碼的程式碼分析簽入原則 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97b321fe5a72c6f3ace680476340eca48f7ed309
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497430"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：以程式碼分析簽入原則強制程式碼的可維護性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 使用程式碼分析簽入原則強制執行維護程式碼](https://docs.microsoft.com/visualstudio/code-quality/how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy)。  
  
開發人員可以使用程式碼度量資訊工具來測量的複雜度和維護的程式碼，但它們無法簽入原則的一部分叫用程式碼度量資訊。 不過，小組可以啟用驗證它們的程式碼的程式碼度量標準合規性和強制透過簽入原則規則的程式碼分析規則。 如需程式碼度量的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。  
  
 繼承深度、 類別結合程度、 可維護性指數和複雜度規則來強制執行容易維護的程式碼，透過程式碼分析簽入原則，可以讓開發人員。 全部四個欄位，這些規則的程式碼分析原則編輯器中，找到 [可維護性規則] 類別下。  
  
 版本的系統管理員控制的[!INCLUDE[esprfound](../includes/esprfound-md.md)]可以加入程式碼分析可維護性規則的簽入原則需求。 這些簽入原則會要求執行程式碼分析簽入初始化之前，根據這些規則變更的開發人員。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>若要開啟 程式碼分析原則編輯器  
  
1.  在**Team Explorer**，以滑鼠右鍵按一下 team 專案，按一下**Team 專案設定**，然後按一下**原始檔控制**。  
  
     **原始檔控制** 對話方塊隨即出現。  
  
2.  在 **簽入原則**索引標籤，然後按一下**新增**。  
  
     **新增簽入原則** 對話方塊隨即出現。  
  
3.  在 **簽入原則**清單中，選取**程式碼分析**核取方塊，然後按一下**確定**。  
  
     **程式碼分析原則編輯器** 對話方塊隨即出現。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>若要啟用程式碼分析可維護性規則  
  
1.  在 **程式碼分析原則編輯器**對話方塊的 **規則設定**，展開**維護性規則**節點。  
  
2.  選取核取方塊，如下列規則：  
  
    -   繼承深度： **CA1501 AvoidExcessiveInheritance** -臨界值： 警告層級的深度超過 5  
  
    -   複雜度： **CA1502 AvoidExcessiveComplexity** -臨界值： 超過 25 項警告  
  
    -   可維護性指數： **ca1505 應 AvoidUnmaintainableCode** -臨界值： 警告少於 20  
  
    -   結合的類別： **CA1506 AvoidExcessiveClassCoupling** -臨界值： 警告在多個類別的 80 和超過 $30 方法  
  
    -   此外，如果您想防止組建將規則違規時，請選取**將警告視為錯誤**規則描述旁邊的核取方塊。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。 新的簽入原則現在適用於未來的簽入。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼度量值](../code-quality/code-metrics-values.md)   
 [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



