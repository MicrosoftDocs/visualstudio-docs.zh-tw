---
title: "CA1824： 以標記組件 NeutralResourcesLanguageAttribute |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824：以 NeutralResourcesLanguageAttribute 標記組件
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 組件包含**ResX**-基礎資源，但沒有<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>套用到它。  
  
## <a name="rule-description"></a>規則描述  
 **NeutralResourcesLanguage**屬性會通知**ResourceManager**用來顯示組件的中性文化特性之資源的語言。 它會在文化特性中性資源語言，與相同的資源查閱時**ResourceManager**會自動使用位於主要組件中的資源。 這會取代搜尋具有目前執行緒的目前使用者介面文化特性的附屬組件。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。  
  
## <a name="fixing-violations"></a>修正違規  
 若要修正此規則的違規情形，將屬性加入至組件，並指定語言的中性文化特性的資源。  
  
## <a name="specifying-the-language"></a>指定的語言  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>若要指定語言的中性文化特性的資源  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**屬性**。  
  
2.  從左側的導覽列中選取**應用程式**，然後按一下 **組件資訊**。  
  
3.  在**組件資訊**對話方塊方塊中，選取語言，從**中性語言**下拉式清單。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它是可以隱藏此規則的警告。 不過，可能會降低啟動效能。