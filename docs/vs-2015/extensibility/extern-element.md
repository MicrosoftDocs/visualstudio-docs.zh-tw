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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204406"
---
# <a name="extern-element"></a>Extern 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extern 元素會參考任何外部標頭 ( .h) 檔案，以便在編譯時期與 .vsct 檔案合併。 要合併的檔案必須位於提供給 .VSCT 編譯器的 Include 路徑上，或是由 [Include 元素](../extensibility/include-element.md)所參考。 檔案可能是其他 .vsct 檔案或 c + + 標頭檔。  
  
 標頭檔中的定義必須是 "#define [Symbol] [Value]" 格式，如果先前已定義，該值可能是另一個符號。 定義可以用於命令專案的條件陳述式中。 所有未實際使用的符號都會被捨棄。  
  
 CommandTable 項目  
Extern 項目  
  
## <a name="syntax"></a>語法  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|href|必要。 標頭檔的路徑：<br /><br /> href = "stdidcmd .h"|  
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
|語言|選擇性。 [\<Strings>](../extensibility/strings-element.md)命令資料表中所有元素的預設語言：<br /><br /> language = "en-us"|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|無。|無。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義 VSPackage 為 IDE 提供的命令（即功能表項目、功能表、工具列和下拉式方塊）的所有元素。|  
  
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
 [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage 如何新增消費者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
