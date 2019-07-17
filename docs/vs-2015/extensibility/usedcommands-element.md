---
title: UsedCommands 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba37458e0f8abca27047574170ab8aa3cc7a44ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186285"
---
# <a name="usedcommands-element"></a>UsedCommands 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UsedCommands 元素分組 UsedCommand 元素和其他 UsedCommands 分組。  
  
 UsedCommands 元素是選擇性的。 如果您未呼叫您的套件之外定義的命令，您不必在.vsct 檔案中加入此區段。  
  
## <a name="syntax"></a>語法  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[UsedCommand 元素](../extensibility/usedcommand-element.md)|其他程式碼實作命令。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表整合式的開發環境 (IDE) 的 VSPackage 提供的命令 （例如，功能表項目、 功能表、 工具列和下拉式方塊） 的所有項目。|  
  
## <a name="example"></a>範例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [UsedCommand 元素](../extensibility/usedcommand-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
