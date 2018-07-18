---
title: VisibilityItem 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143461"
---
# <a name="visibilityitem-element"></a>VisibilityItem 項目
`VisibilityItem`元素會決定的命令和工具列靜態的可見性。 每個項目會識別命令或功能表上，以及相關聯的命令 UI 內容。 Visual Studio 會偵測命令、 功能表和工具列和其可見性，而不必載入定義它們的 Vspackage。 IDE 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法來判斷命令 UI 內容是否為作用中。  
  
 Visual Studio 載入 VSPackage 之後，預期要由 VSPackage 的命令可見性而非`VisibilityItem`。 若要判斷命令的可見性，您可以實作<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>事件處理常式或<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，會根據您的命令的實作方式。  
  
 命令或功能表具有`VisibilityItem`項目會顯示相關聯的內容時才使用中。 您可以使單一命令、 功能表或工具列與一或多個命令 UI 內容包括每個命令內容組合的項目。 如果多個命令 UI 內容與相關聯的命令或功能表，然後命令或功能表時顯示相關聯的命令 UI 任何的內容一個是作用中。  
  
 `VisibilityItem`項目只適用於命令、 功能表和工具列，不到群組。 沒有相關的項目`VisibilityItem`項目是可見的只要其父功能表在作用中。  
  
## <a name="syntax"></a>語法  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼命令識別項的識別碼。|  
|內容|必要。 此命令會顯示 UI 內容。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`元素決定靜態群組的命令和工具列是否可見。|  
  
## <a name="remarks"></a>備註  
 中所定義的標準 Visual Studio UI 內容*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\vsshlids.h 檔案以及在<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>和<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>類別。 一組更完整的 UI 內容定義於<xref:Microsoft.VisualStudio.VSConstants>類別。  
  
## <a name="example"></a>範例  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 項目](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)