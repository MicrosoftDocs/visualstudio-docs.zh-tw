---
title: "Ca1308： 必須將字串標準化為大寫字母 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9064ca9861f609499971b9f5188f5b0006458c15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308：必須將字串標準化為大寫字母
|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 作業會正規化為小寫的字串。  
  
## <a name="rule-description"></a>規則描述  
 字串應該標準化為大寫字母。 小組的字元，它們會轉換成小寫字母時，無法構成來回行程。 若要進行來回轉換字元從一個地區設定為以不同的方式，代表字元資料的另一個地區設定，然後以精確地表示會從已轉換的字元擷取原始字元。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 變更操作，將字串轉換成小寫，以便將字串轉換成改為大寫。 例如，變更`String.ToLower(CultureInfo.InvariantCulture)`至`String.ToUpper(CultureInfo.InvariantCulture)`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可安全地隱藏警告訊息，當您不會進行安全性決策 （例如，當您要將它顯示在 UI 中） 的結果。  
  
## <a name="see-also"></a>請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)