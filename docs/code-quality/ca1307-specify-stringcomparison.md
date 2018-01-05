---
title: "CA1307： 指定 StringComparison |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7087cfe23f7911ec33891a70cd88cf47ee9e4a7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307：指定 StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 字串比較作業使用的方法多載不會設定<xref:System.StringComparison>參數。  
  
## <a name="rule-description"></a>規則描述  
 許多字串作業，最重要<xref:System.String.Compare%2A>和<xref:System.String.Equals%2A>方法，提供可接受的多載<xref:System.StringComparison>做為參數的列舉值。  
  
 每當有多載存在該採用<xref:System.StringComparison>參數，它應該用來取代不接受此參數的多載。 藉由明確設定此參數，通常的程式碼就會較清楚、 更容易維護。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更的字串比較方法多載，可接受<xref:System.StringComparison>列舉型別做為參數。 例如： 變更`String.Compare(str1, str2)`至`String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，當程式庫或應用程式適用於有限制的本機使用者，並因此不會當地語系化。  
  
## <a name="see-also"></a>請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1309：使用循序的 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)