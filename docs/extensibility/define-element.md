---
title: 定義項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2596023628086ce5e921eeb8499956828d4c8a5c
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497157"
---
# <a name="define-element"></a>定義項目
定義的符號名稱和值組。 這個符號可以評估的條件式屬性。 如需詳細資訊，請參閱 <<c0> [ 條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另請參閱[Symbols 元素](../extensibility/symbols-element.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要。 符號名稱：<br /><br /> 名稱 = 「 模式 」|  
|value|必要。 符號的值：<br /><br /> 值 = 「 標準 」|  
|條件|選擇性。 如需詳細資訊，請參閱 <<c0> [ 條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的 VSPackage 提供整合式的開發環境 (IDE) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
  
## <a name="example"></a>範例  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)