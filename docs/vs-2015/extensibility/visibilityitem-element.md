---
title: VisibilityItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 46f8d4557c5abcc14963a87cd8c90217abd3ab1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209452"
---
# <a name="visibilityitem-element"></a>VisibilityItem 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VisibilityItem`元素會決定的命令和工具列靜態的可見性。 命令或功能表上，以及相關聯的命令 UI 內容，就會識別每個項目。 Visual Studio 會偵測命令、 功能表和工具列和其可見性，而不必載入 Vspackage，在定義它們。 IDE 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法，以判斷是否為作用中命令 UI 內容。  
  
 Visual Studio 在載入 VSPackage 之後，要求命令可見性取決於 VSPackage 而不是`VisibilityItem`。 若要判斷您的命令可見性，您可以實作<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>事件處理常式或<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，取決於您如何實作您的命令。  
  
 命令或具有功能表`VisibilityItem`項目會顯示相關聯的內容時才使用中。 您可以與一個或多個命令 UI 內容關聯的單一命令、 功能表或工具列，包含每個命令內容組合的項目。 如果命令或功能表是多個命令 UI 內容相關聯，然後命令或功能表會顯示相關聯的命令 UI 任何的內容一個使用中時。  
  
 `VisibilityItem`項目僅適用於命令、 功能表和工具列，不到群組。 沒有相關的項目`VisibilityItem`父功能表在作用中時，會顯示項目。  
  
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
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼的命令識別項的識別碼。|  
|內容|必要。 此命令會顯示 UI 內容。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`元素會決定群組的命令和工具列的靜態的可見性。|  
  
## <a name="remarks"></a>備註  
 中所定義的標準的 Visual Studio UI 內容*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\vsshlids.h 檔案也如同<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>和<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>類別。 一組更完整的 UI 內容定義於<xref:Microsoft.VisualStudio.VSConstants>類別。  
  
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
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

