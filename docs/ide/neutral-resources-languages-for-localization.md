---
title: "當地語系化的中性資源語言 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文化特性, 找出資源"
  - "全球化 [Visual Studio], 資源"
  - "當地語系化 [Visual Studio], 資源"
  - "中性資源"
  - "NeutralResourcesLanguageAttribute 類別"
  - "資源 [Visual Studio], 回溯系統"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# 當地語系化的中性資源語言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> 類別會指定主要組件中所包含之資源的文化特性。  這個屬性 \(Attribute\) 是用來提升效能，讓 <xref:System.Resources.ResourceManager> 物件不需要搜尋主要組件中所包含的資源。  
  
 下列程式碼顯示如何設定中性資源語言。  您可將這段程式碼放入建置指令碼或是 AssemblyInfo.vb 或 AssemblyInfo.cs 檔中。  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## 請參閱  
 <xref:System.Resources.ResourceManager>   
 [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [階層式組織當地語系化的資源](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [當地語系化應用程式](../ide/localizing-applications.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)