---
title: Extern 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204406"
---
# <a name="extern-element"></a>Extern 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extern 元素會參考在編譯時期合併使用.vsct 檔的任何外部標頭 (.h) 檔案。 要合併的檔案必須位於 Include 路徑指定給 VSCT 編譯器，或是參照[包含的項目](../extensibility/include-element.md)。 檔案可能是其他.vsct 檔案或C++標頭檔。  
  
 標頭檔中的定義的格式必須是"#define [符號] [Value]"的值可能是另一個符號，如果先前已定義。 定義可用於條件陳述式的命令項目。 將捨棄任何並未實際使用的符號。  
  
 CommandTable 項目  
Extern 項目  
  
## <a name="syntax"></a>語法  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|href|必要項。 標頭檔路徑：<br /><br /> href="stdidcmd.h"|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
|語言|選擇性。 所有的預設語言[\<字串 >](../extensibility/strings-element.md)命令表中的項目：<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|無。|無。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義所有代表命令的項目 — 也就是功能表項目、 功能表、 工具列和下拉式方塊，VSPackage 提供給 IDE。|  
  
## <a name="example"></a>範例  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
