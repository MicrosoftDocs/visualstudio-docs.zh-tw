---
title: "CA1058：類型不應該擴充特定的基底類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1058：類型不應該擴充特定的基底類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的型別會延伸某些基底型別 \(Base Type\)。  這項規則目前會報告衍生自下列型別的型別：  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## 規則描述  
 若是 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 1 版，建議從 <xref:System.ApplicationException> 衍生新的例外狀況。  建議已變更，而新的例外狀況應該衍生自 <xref:System.Exception?displayProperty=fullName> 或在 <xref:System> 命名空間中的其中一個子類別 \(Subclass\)。  
  
 如果您想建立基礎物件模型或資料來源的 XML 檢視，請勿建立 <xref:System.Xml.XmlDocument> 的子類別。  
  
### 非泛型集合  
 請盡量使用和 \(或\) 擴充泛型集合。  除非過去曾經發行過，否則請勿在程式碼中擴充非泛型集合。  
  
 **不正確使用的範例**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **正確使用的範例**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## 如何修正違規  
 若要修正這項規則的違規情形，請從其他基底型別或泛型集合來衍生型別。  
  
## 隱藏警告的時機  
 對於 <xref:System.ApplicationException> 的違規情形，請勿隱藏此規則的警告。  對於 <xref:System.Xml.XmlDocument> 的相關違規情形，請放心地隱藏此規則的警告。  如果事先已經發行過程式碼，則可以放心地隱藏關於非泛型集合的警告。