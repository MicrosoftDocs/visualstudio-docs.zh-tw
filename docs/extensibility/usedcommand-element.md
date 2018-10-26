---
title: UsedCommand 元素 |Microsoft Docs
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
ms.openlocfilehash: 4f7df36c05de0d8dc2f68ab8e41afa11366276b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856297"
---
# <a name="usedcommand-element"></a>UsedCommand 項目
可讓 VSPackage 也可以存取另一個.vsct 檔案中定義的命令。 例如，如果您的 VSPackage 會使用標準**複製**命令，可定義[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]shell 中，您可以將命令加入功能表或工具列而不需要重新實作它。  
  
## <a name="syntax"></a>語法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 識別命令的 GUID 識別碼組的 GUID。|  
|id|必要。 識別命令的 GUID 識別碼組識別碼。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|群組 UsedCommand 元素，而且其他 UsedCommands 分組。|  
  
## <a name="remarks"></a>備註  
 將命令新增至`<UsedCommands>`元素，VSPackage 會通知[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage，需要此命令的環境。 您應該加入`<UsedCommand>`封裝需要的任何命令的項目可能不會包含於所有版本的 Visual Studio 的設定。 例如，如果您的封裝呼叫 Visual c + + 特定的命令，命令將無法供 Visual Web Developer 中的使用者除非您包含`<UsedCommand>`命令的項目。  
  
## <a name="example"></a>範例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)