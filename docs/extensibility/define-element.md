---
title: "定義項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b435c4e44391bbf477ed94fa96ee382613290530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="define-element"></a>定義項目
定義的符號名稱和值組。 這個符號可以來評估條件式屬性。 如需詳細資訊，請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另請參閱[符號項目](../extensibility/symbols-element.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要項。 符號名稱：<br /><br /> 名稱 ="Mode"|  
|值|必要項。 符號的值：<br /><br /> 值 ="Standard"|  
|條件|選擇項。 如需詳細資訊，請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供的命令到整合式的開發環境 (IDE) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
  
## <a name="example"></a>範例  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)