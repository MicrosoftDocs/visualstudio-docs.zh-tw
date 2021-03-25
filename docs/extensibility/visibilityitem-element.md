---
title: VisibilityItem 元素 |Microsoft Docs
description: VisibilityItem 元素決定命令和工具列的靜態可見度。 專案會識別命令或功能表，以及相關聯的命令 UI 內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1229c5e63838a8192c7622cdddd9881799a2da11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062508"
---
# <a name="visibilityitem-element"></a>VisibilityItem 元素
`VisibilityItem`元素會決定命令和工具列的靜態可見度。 每個專案都會識別命令或功能表，以及相關聯的命令 UI 內容。 Visual Studio 會偵測命令、功能表和工具列，以及它們的可見度，而不會載入定義它們的 Vspackage。 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 會使用方法來判斷命令 UI 內容是否為作用中。

 載入 VSPackage 之後，Visual Studio 預期會由 VSPackage 判斷命令可見度，而不是 `VisibilityItem` 。 若要判斷您的命令可見度，您可以 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 根據您執行命令的方式，執行事件處理常式或 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。

 `VisibilityItem`只有當相關聯的內容為作用中時，才會顯示具有元素的命令或功能表。 您可以針對每個命令內容組合包含一個專案，藉此將單一命令、功能表或工具列與一個或多個命令 UI 內容產生關聯。 如果命令或功能表與多個命令 UI 內容相關聯，當任何一個相關聯的命令 UI 內容為作用中時，就會顯示命令或功能表。

 `VisibilityItem`元素只適用于命令、功能表和工具列，而不會套用至群組。 只要專案的 `VisibilityItem` 父功能表為使用中，就會顯示沒有相關專案的元素。

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|
|內容|必要。 可以看見命令的 UI 內容。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素
 無

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`元素會決定命令和工具列群組的靜態可見度。|

## <a name="remarks"></a>備註
 標準 Visual Studio UI 內容是在 *VISUAL STUDIO SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\vsshlids.h 檔以及 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> 和類別中定義 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 。 類別中會定義一組更完整的 UI 內容 <xref:Microsoft.VisualStudio.VSConstants> 。

## <a name="example"></a>範例

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)
- [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
