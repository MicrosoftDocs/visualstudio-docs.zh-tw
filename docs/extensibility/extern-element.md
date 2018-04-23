---
title: Extern 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea14d985265d02c3e60ee12c8b46deafba2bcd72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="extern-element"></a>Extern 項目
Extern 項目會參考在編譯時期與.vsct 檔案合併的任何外部標頭 (.h) 檔案。 要合併的檔案必須是指定給 VSCT 編譯器或所參考的 Include 路徑上[Include 項目](../extensibility/include-element.md)。 檔案可能是其他.vsct 檔案或 c + + 標頭檔。  
  
 標頭檔中的定義的格式必須是"#define [符號] [Value]"的值可能是另一個符號，如果先前已定義。 定義可用於條件陳述式的命令項目。 將捨棄實際上不會使用任何符號。  
  
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
|href|必要。 標頭檔的路徑：<br /><br /> href="stdidcmd.h"|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
|語言|選擇性。 所有的預設語言[\<字串 >](../extensibility/strings-element.md)命令表中的項目：<br /><br /> 語言 ="en-我們"|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|無。|無。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義的所有項目代表命令 — 也就是功能表項目、 功能表、 工具列和下拉式方塊 — VSPackage 提供給 IDE。|  
  
## <a name="example"></a>範例  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)