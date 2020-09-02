---
title: UsedCommand 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186372"
---
# <a name="usedcommand-element"></a>UsedCommand 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

讓 VSPackage 存取另一個 .vsct 檔案中定義的命令。 例如，如果您的 VSPackage 使用由 shell 定義的標準 **複製** 命令， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 您可以將命令新增至功能表或工具列，而不需要重新執行它。  
  
## <a name="syntax"></a>語法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 識別命令之 GUID 識別碼組的 GUID。|  
|id|必要。 識別命令之 GUID 識別碼組的識別碼。|  
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|群組 UsedCommand 元素和其他 UsedCommands 群組。|  
  
## <a name="remarks"></a>備註  
 藉由將命令新增至 `<UsedCommands>` 元素，VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 就會通知環境 VSPackage 需要命令。 您應該 `<UsedCommand>` 為套件需要的任何命令新增專案，而這些命令可能不會包含在 Visual Studio 的所有版本和設定中。 例如，如果您的封裝呼叫 Visual C++ 特有的命令，則 Visual Web Developer 的使用者將無法使用此命令，除非您包含 `<UsedCommand>` 命令的元素。  
  
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
