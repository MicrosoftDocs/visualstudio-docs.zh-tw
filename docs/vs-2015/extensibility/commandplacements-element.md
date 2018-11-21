---
title: CommandPlacements 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18c165f978ab43909d484ff13edd1d7d2ddd0f60
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782059"
---
# <a name="commandplacements-element"></a>CommandPlacements 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandPlacements 元素分組 CommandPlacement 元素和其他 CommandPlacements 分組。  
  
 CommandPlacements 元素是選擇性的。 如果任何命令、 群組或功能表必須包含在次要位置中，您不必在.vsct 檔案中加入此區段。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|CommandPlacements|群組 CommandPlacement 元素，而且其他 CommandPlacements 分組。|  
|[CommandPlacement 元素](../extensibility/commandplacement-element.md)|可讓按鈕、 群組和包含在一個以上的群組或功能表的功能表。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的所有項目。|  
  
## <a name="example"></a>範例  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>另請參閱  
 [CommandPlacement 元素](../extensibility/commandplacement-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

