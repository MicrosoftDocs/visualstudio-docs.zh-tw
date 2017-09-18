---
title: "包含項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "包含項目 (VSCT XML 結構描述)"
  - "VSCT XML 結構描述項目包括"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 包含項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含項目會指定可以找到的檔案所提供包含可插入至目前檔案的路徑。  所有符號和定義的型別都會在已編譯的結果。  
  
## 語法  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|href|必要項。 標頭檔的路徑:<br /><br /> href\="stdidcmd.h 」|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無。|無。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義的所有項目代表命令 — 也就是功能表項目、 功能表、 工具列和下拉式方塊 — VSPackage 提供 ide。|  
  
## 範例  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)