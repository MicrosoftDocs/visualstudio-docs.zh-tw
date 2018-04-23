---
title: UsedCommand 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4888733abf142f6582706406decbea0bf84ce519
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="usedcommand-element"></a>UsedCommand 項目
可讓 VSPackage 也可以存取另一個.vsct 檔案中定義的命令。 例如，如果您的 VSPackage 使用標準**複製**命令，由定義[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]shell 中，您可以將命令加入功能表或工具列而不重新實作它。  
  
## <a name="syntax"></a>語法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 識別命令的 GUID 識別碼組的 GUID。|  
|id|必要。 識別命令的 GUID 識別碼組識別碼。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|群組 UsedCommand 項目和其他 UsedCommands 群組。|  
  
## <a name="remarks"></a>備註  
 將命令新增至`<UsedCommands>`項目，VSPackage 會通知[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境 VSPackage 需要的命令。 您應該加入`<UsedCommand>`套件需要的任何命令項目可能不會包含在所有版本和 Visual studio 的設定。 比方說，如果您的封裝呼叫 Visual c + + 特有的命令，命令將無法使用的 Visual Web Developer 使用者除非您包含`<UsedCommand>`命令項目。  
  
## <a name="example"></a>範例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [UsedCommands 項目](../extensibility/usedcommands-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)